以下代码经过测试通过，系统centos 6.3  


## 一、匹配或

sed 匹配100_1000或bigger_1000  
```
sed -n '/100_1000\|bigger_1000/p' 20160220  
sed -n '/\(100_1000\|bigger_1000\)/p' 20160220  
```   

awk匹配100_1000或bigger_1000  
默认是$0匹配，所以写不写均可  

```
awk '/100_1000/||/bigger_1000/{print $0}' 20160220 | head
awk '$0~/100_1000/||/bigger_1000/{print $0}' 20160220 | head
```  

grep匹配100_1000或bigger_1000 -E选项表示扩展的正则表达式    
```
grep -E '(100_1000|bigger_1000)' 20160220 | head
```  

## 二、匹配与

sed匹配与  
```
sed -n '/19000/{/100_1000/p}' 20160220 | head
```  

awk匹配与    
```
awk '/19000/&&/100_1000/{print $0}' 20160220 | head
awk '$0~/19000/&&/100_1000/{print $0}' 20160220 | head
```  

grep匹配与    
```
grep -E '(19000.*100_1000|100_1000.*19000)' 20160220 | head
```  

