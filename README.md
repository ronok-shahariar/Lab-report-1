# Lab-report-1
# Experiment No 14
## Name of the Experiment
Study Of Newton Backward Difference Method To Predict Unknown Value(s) For Any Geographic Point Data.
## Objectives
The objective of this experiment is to use Newton backward difference method to find out the very precise values of the given data point, using MATLAB. 
## Theory
The differences **_y1 – y0, y2 – y1, ……, yn – yn–1_** when denoted by **_dy1, dy2, ……, dyn_**, respectively, are called first backward difference. Thus the first backward differences are **_[1]_**: 

![1](https://user-images.githubusercontent.com/51051408/105453897-35666c80-5cab-11eb-908b-555e06a561db.jpg)

NEWTON’S GREGORY BACKWARD INTERPOLATION FORMULA **_[1]_**:

![2](https://user-images.githubusercontent.com/51051408/105454195-a9a11000-5cab-11eb-8a88-07c60493d115.jpg)
## Tool
>MATLAB Software ver. 16.01
## MATLAB Code
[With comments](http://www.github.com)
- Given values
```
x=[1921 1931 1941 1951 1961 1971 1981];
fx=[35 42 58 84 120 165 220];

```
- array of zeros
```
dt=zeros(n,n)
```
- inserting x and fx in dt
```
for i=1:n
    dt(i,1)=x(i);
    dt(i,2)=fx(i);
end

```
- creating Newton backward difference table
```
z=3;k=2;
for i=1:n-1   
   for j=k:n
        dt(j,z)=(dt(i+1,z-1)-dt(i,z-1));
        i=i+1;
        if(i>=n)
            break;
        end
   end
   k=k+1;z=z+1;    
end
```
- value for fx to find
```
x_int=1975;
```
- determining u=(x-x1)*h
```
u=(x_int-x(n))/(x(2)-x(1));
```
- determining sum by formula
```
y_sum=dt(n,2);k=1;d=1;
for i=2:4   
    for j=0:i-2 
        d=d*(u + j);
        k=k*(j+1);
    end
    y_sum=y_sum+(dt(n,i+1)/k)*d;
    d=1;
    dt(n,i+1);
end
```
- result
```
dt
y_sum
%% ploting the graph
plot(x, fx, 'bo', x_int, y_sum, 'r*')
axis([1900 2000 0 250])
xlabel('x')
ylabel('y')
```
## Output
![3](https://user-images.githubusercontent.com/51051408/105455514-ccccbf00-5cad-11eb-995c-f98477cdee22.jpg)

![4](https://user-images.githubusercontent.com/51051408/105455537-d9e9ae00-5cad-11eb-8b3c-fcd9adb04ece.jpg)

>Figure 14.1: Table of Newton Backward Difference

![5](https://user-images.githubusercontent.com/51051408/105455602-f84fa980-5cad-11eb-8a98-30e0448b22d7.jpg)

>Figure 14.2: Graph Of The Function
## Result(s)& Discussion
The unknown values for **x = 1975**  is **y = 185.7720** . From text book **_[2]_** for **x=1975 is y=185.8=186(round)**
## Conclusion
We have found the approximate unknown value for **1975** which is same as text book **_[2]_**. Matlab read the exact result **185.7720**.
## References
[1] https://www.geeksforgeeks.org/newton-forward-backward-interpolation/

[2] C. Chapra and P. Canale Raymond , “Numerical Methods for Engineers”, 7th ed. McGraw-Hill Education, 2 Penn Plaza, New York, NY 10121, 2015





