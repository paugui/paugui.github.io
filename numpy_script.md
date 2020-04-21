# Installation


```python
#conda install numpy
#pip3 install numpy

import numpy as np
```

# Numpy Arrays

A homogeneous container of numerical elements. Each element can be a numerical element of a single type (such as float, int or complex) or a combination (such as (float, int, float)). Each array has an associated data-type (or dtype), which describes the numerical type of its elements.

Axes are defined for arrays with more than one dimension. A 2-dimensional array has two corresponding axes: the first running vertically downwards across rows (axis 0), and the second running horizontally across columns (axis 1).


## Creating NumPy Arrays


```python
#From a Python list

my_list = [1,2,3]
my_list

arr = np.array(my_list)
arr
```




>> array([1, 2, 3])




```python
#From a Python matrix

my_matrix = [[1,2,3],[4,5,6],[7,8,9]]
my_matrix

mat = np.array(my_matrix)
mat
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])



## Array
np.array(object [, dtype=None, copy=True, order='K', subok=False, ndmin=0])


```python
#create an array 1 dimension
arr = np.array([2,4,6]) 
print(arr)
```

    [2 4 6]
    


```python
#create an array 2 dimensions
mat = np.array([[2,4,6], [8,10,12], [14,16,18]]) 
print(mat)
```

    [[ 2  4  6]
     [ 8 10 12]
     [14 16 18]]
    

### zeros and ones


```python
#generates arrays of zeros
arr0 = np.zeros(3)
mat0 = np.zeros((5,5))
mat0
```




    array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])




```python
#generates arrays of ones
arr1 = np.ones(3)
mat1 = np.ones((3,3))
mat1
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])



## arange array

np.arange(start, stop, [step, ]dtype=None)


```python
#create sequences of numbers
arr = np.arange(0,10, 2, int ) #np.arange([start,] stop [, step, dtype])
arr

arr = np.arange( 0, 2, 0.3 ) #accepts float
arr

arr = np.arange(0,12).reshape(3,4) #can be reshaped in rows and columns
arr
```




    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11]])



## linspace
np.linspace(start, stop, num=50[, endpoint=True, retstep=False, dtype=None, axis=0])


```python
#Return evenly spaced numbers over a specified interval
np.linspace(0,10,3)
np.linspace(0,10,21)
```




    array([ 0. ,  0.5,  1. ,  1.5,  2. ,  2.5,  3. ,  3.5,  4. ,  4.5,  5. ,
            5.5,  6. ,  6.5,  7. ,  7.5,  8. ,  8.5,  9. ,  9.5, 10. ])



## eye


```python
#creates an identity matrix
np.eye(4)
```




    array([[1., 0., 0., 0.],
           [0., 1., 0., 0.],
           [0., 0., 1., 0.],
           [0., 0., 0., 1.]])



## Random 


```python
#Create an array of the given shape and populate it with random samples from a uniform distribution over [0, 1].
np.random.rand(2)
np.random.rand(5,5)

#Return a sample (or samples) from the "standard normal" distribution. Unlike rand which is uniform:
np.random.randn(2)
np.random.randn(5,5)

#Return random integers from `low` (inclusive) to `high` (exclusive).
np.random.randint(1,100)
np.random.randint(1,100,10)
```




    array([35, 47, 34, 63, 71, 40, 72, 68, 92, 39])



## Array Attributes and Methods


```python
arr = np.arange(25)
arr #show

ranarr = np.random.randint(0,50,10)
ranarr #show
```




    array([ 6,  3, 20, 44, 41,  7, 38, 41, 11, 31])




```python
ranarr.reshape(5,2) #modify the structure of the array
```




    array([[ 6,  3],
           [20, 44],
           [41,  7],
           [38, 41],
           [11, 31]])




```python
ranarr.max() #max value
ranarr.argmax() #max value position

ranarr.min()#min value
ranarr.argmin() #min value position
```




    8




```python
ranarr.ndim #number of axes(dimensions)
ranarr.size #number of elements
ranarr.shape #dimensions
ranarr.dtype #data type
ranarr.itemsize #size in bytes
```




    1




```python
ranarr.reshape(5,2).shape
```




    (5, 2)



# Indexing and Selection

## Bracket Indexing and Selection



```python
#Get a value at an index
arr[8]

#Get values in a range
arr[1:5]

#To get a copy, need to be explicit
arr_copy = arr.copy()
arr_copy

#Copies and clones
arr1 = arr
arr2 = arr.copy
arr is arr1 #true, same object
arr is arr2 #false, different object
```




    False



### Indexing a 2D array (matrices)


```python
#Creating 2D array
arr_2d = np.array(([5,10,15],[20,25,30],[35,40,45]))
arr_2d

#Indexing rows
arr_2d[1]
arr_2d[[0,2]]

# Getting individual element value
arr_2d[1][0]

#Shape (2,2) from top right corner
arr_2d[:2,1:]
```




    array([[10, 15],
           [25, 30]])




```python
#Filter
arr = np.arange(1,11)
arr > 4
bool_arr = arr>4
arr[bool_arr]

arr[arr>2]

x = 2
arr[arr>x]
```




    array([ 3,  4,  5,  6,  7,  8,  9, 10])



## NumPy Operations

### Arithmetic


```python
arr = np.arange(1,13).reshape(3,4)
print(arr)
```

    [[ 1  2  3  4]
     [ 5  6  7  8]
     [ 9 10 11 12]]
    


```python
#basic operations
arr + arr #sum
arr - arr #subtraction
arr * arr #product
arr/arr #division

1/arr #normalization
arr**2 #power

np.sqrt(arr) #square root
np.exp(arr) #exponent

np.sin(arr) #sin
np.log(arr) #logaritm
```




    479001600




```python
#sumas
np.sum(arr) #total sum

np.sum(arr, axis = 0) #column sum
np.sum(arr, axis = 1) #row sum

np.cumsum(arr, axis = 0) #cumulative column sum
np.cumsum(arr, axis = 1) #cumulative row sum
```




    array([10, 26, 42])




```python
#diference
np.diff(arr) #diference between a number and the following one
```




    array([[1, 1, 1],
           [1, 1, 1],
           [1, 1, 1]])




```python
#product
np.prod(arr) #total product
np.cumprod(arr) #acumulated product
```


```python
#basic statistics
np.max(arr) #maximum
np.min(arr) #minimum

np.average(arr) #average
np.mean(arr) #mean
np.median(arr) #median

np.var(arr) #variance
np.std(arr) #standard deviation
np.bincount(arr[0]) #values occurency

np.corrcoef(arr) #Pearson relation between vectprs
np.cov(arr) #covariance matrix
```




    11.916666666666666




```python
#rounding methods
arrdem = np.arange(0,8,0.23)
arrdem

np.rint(arrdem) #to the nearest integer
np.round(arrdem, 1) #to the nearest number for the precision defined (decimals)
np.ceil(arrdem) #to te nearest upper integer
np.floor(arrdem) #to te nearest lower integer

np.trunc(arrdem) #truncates to integer
np.clip(arrdem, 2, 6) #clips lower and upper values according to the boundaries
```




    array([2.  , 2.  , 2.  , 2.  , 2.  , 2.  , 2.  , 2.  , 2.  , 2.07, 2.3 ,
           2.53, 2.76, 2.99, 3.22, 3.45, 3.68, 3.91, 4.14, 4.37, 4.6 , 4.83,
           5.06, 5.29, 5.52, 5.75, 5.98, 6.  , 6.  , 6.  , 6.  , 6.  , 6.  ,
           6.  , 6.  ])



## Shape manipulation


```python
#Shape manipulation
np.sort(arr) #sort values

np.ravel(arr) #flattens the values to a single line
arr.T #transposes the matrix
arr.resize(4,3) #modifies arrays structure

np.vstack((arr, arr)) #joins vertically (rows)
np.hstack((arr,arr)) #joins horizontally (columns)

np.split(arr, 2) #splits in equal parts the rows
np.hsplit(arr, 3) #splits in equal parts the columns
```




    [array([[ 1],
            [ 4],
            [ 7],
            [10]]), array([[ 2],
            [ 5],
            [ 8],
            [11]]), array([[ 3],
            [ 6],
            [ 9],
            [12]])]



## Broadcasting


```python
arr[0:3,0] = 100 #updates values
arr

slice_of_arr = arr[:2, :3] #cuts a portion of values
slice_of_arr

arr[arr > 6] = 20 #filter to update
arr
```




    array([[20,  2,  3,  4],
           [20,  6, 20, 20],
           [20, 20, 20, 20]])



For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
