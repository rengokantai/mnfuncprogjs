### mnfuncprogjs
####Chapter 1. Becoming functional
#####1.2. What is functional programming?
######1.2.3. Referential transparency and substitutability


######1.2.4. Preserving immutable data
arrays, aren’t immutable; even if they’re passed as input to a function.
```
var sortDesc = function (arr) {
  return arr.sort(function (a, b) {
     return b - a;
  });
}
```
The Array.sort function is stateful and causes the side effect of sorting the array in place—the original reference is changed.


#####1.3. Benefits of functional programming
```
f • g = f(g(x))
```
This formula reads “f composed of g,” which creates a loose, type-safe relationship between g’s return value and f’s argument.  
convert old code to RxJS:
```
var valid = false;
var elem = document.querySelector("");
elem.onkeyup= function(e){
  var v = elem.value;
  if(v!==null &&v.length!==0){
    v =v.replace(/^\s+|\s+$|\-/g,'');
    if(v.length===9){
      valid=true;
    }
  }
}
```
RxJS:
```
Rx.Observable.fromEvent(document.querySelector(''), 'keyup')
   .map(input => input.srcElement.value)
   .filter(v => v !== null && v.length !== 0)
   .map(v => v.replace(/^\s*|\s*$|\-/g, ''))
   .skipWhile(v => v.length !== 9)
   .subscribe(
      v => console.log(``)
    );
```
####Chapter 2. Higher-order JavaScript
#####2.1. Why JavaScript?
######2.2. Functional vs. object-oriented programming
object:
```
var person = new Student('ke');
```
oo:
```
get fullName(){
return this.name;
}
```
func:
```
var fullname = person => person.name;
```
impl:  
oo
```
person.fullName()
```
func:
```
fullname(person);
```

####Chapter 3. Few data structures, many operations
######3.3.1. Understanding lambda expressions
######3.3.3. Gathering results with _.reduce
