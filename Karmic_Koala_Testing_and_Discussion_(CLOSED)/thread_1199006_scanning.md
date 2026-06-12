---
title: "scanning"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-06-28
is sane or xsane aware of networked scanners ? I have a brother mfc 7440n , it is detected and prints fine as either a network printer or if I plug it in via the usb connection but (x)sane only sees it if the usb cable is pulgged in , if I try to connect over the network it says no devices available . This is not just with karmic but also with hardy or jaunty .

---

### Post by ronacc on 2009-07-01
problem solved , the brother scanner driver needed to be configured with the IP address of the scanner . see reply from brother below .
```
Would you please try to run the following command?
 
brsaneconfig3 -a name=scanner model=MFC-7440N ip=xx.xx.xx.xx
(Type your MFC's ip address for xx.xx.xx.xx part)
 
We have to tell brscan3 the network scanner's model and ip with that
command.
 
Please see the step 5 in the following website as a reference.
http://solutions.brother.com/linux/en_us/instruction_scn1b.html
 
```
I also posted this in another area of the forums since a search showed several threads about this with various makes of scanner .

---

### Post by pdcorcoran on 2009-09-05
> **ronacc said:**
> problem solved , the brother scanner driver needed to be configured with the IP address of the scanner . see reply from brother below .
```
Would you please try to run the following command?
 
brsaneconfig3 -a name=scanner model=MFC-7440N ip=xx.xx.xx.xx
(Type your MFC's ip address for xx.xx.xx.xx part)
 
We have to tell brscan3 the network scanner's model and ip with that
command.
 
Please see the step 5 in the following website as a reference.
http://solutions.brother.com/linux/en_us/instruction_scn1b.html
 
```I also posted this in another area of the forums since a search showed several threads about this with various makes of scanner .


I used the brsaneconfig3 command and  got this:

pdc@ubuntu:~$ sudo brsaneconfig3 -q | grep scanner
  0 scanner             "MFC-7840W"         I:192.168.1.19

However, xsane reports no scanner found.  What else do I need to do?

---

