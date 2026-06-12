---
title: "PDF Chain ERROR: PDFTK PDFTK returns an error"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by baumtopf on 2011-06-22
Hello Ubuntu Users,

I get following problem. I installed PDF Chain with Ubuntu Software Center. But if I merge these PDF - Files often this error message comes: 

> PDF Chain ERROR: PDFTK PDFTK returns an error 


and then the PDF - Files are no merged. 

Alternativ I used PDFTK to merge these files. But then this Error message comes

> 
baumtopf@ubuntu:~$ cd Desktop/test baumtopf@ubuntu:~/Desktop/test$ pdftk aaa.pdf bbb.pdf ccc.pdf ddd.pdf eee.pdf fff.pdf ggg.pdf cat output gesamt.pdf Unhandled Java Exception: Unhandled Java Exception: java.lang.NullPointerException    at gnu.gcj.runtime.NameFinder.lookup(libgcj.so.11)    at java.lang.VMThrowable.getStackTrace(libgcj.so.11)    at java.lang.Throwable.getStackTrace(libgcj.so.11)    at java.lang.Throwable.stackTraceString(libgcj.so.11)    at java.lang.Throwable.printStackTrace(libgcj.so.11)    at java.lang.Throwable.printStackTrace(libgcj.so.11) baumtopf@ubuntu:~/Desktop/test$ 
This error is for me unpretictable. I cannot explain when this error comes and when not. I thought my pdf files are too large, because one file of these is often bigger than 1 MB. But this was not the reason, because later I merged new PDF files and they are also bigger than 1 MB. 

Alternativ I used PDF Shuffler. And with this programme I could merge these. But I would like to use PDF Chain or at least PDFTK, because they have more options. What can I do to solve this problem?

Regard Juergen

---

### Post by baumtopf on 2011-06-24
Hello Ubuntu Users,

perhaps you don't understand my problem with PDF-Files, so I created a video and uploaded on youtube.
Please watch: 

[http://www.youtube.com/watch?v=_8KYtwC8tDY](http://www.youtube.com/watch?v=_8KYtwC8tDY)

Error message again:

> 
Unhandled Java Exception:
Unhandled Java Exception:
java.lang.NullPointerException
   at gnu.gcj.runtime.NameFinder.lookup(NameFinder.java:201)
   at java.lang.VMThrowable.getStackTrace(natVMThrowable.cc:44)
   at java.lang.Throwable.getStackTrace(Throwable.java:524)
   at java.lang.Throwable.stackTraceString(Throwable.java:419)
   at java.lang.Throwable.printStackTrace(Throwable.java:365)
   at java.lang.Throwable.printStackTrace(Throwable.java:354)


I get a trying to solve this problem from this soure:

[http://fossplanet.com/f10/%5Bbug-779908%5D-%5Bnew%5D-pdftk-fails-output-option-161767/](http://fossplanet.com/f10/%5Bbug-779908%5D-%5Bnew%5D-pdftk-fails-output-option-161767/)

I tried to set the output into other directory where the input files are not stay. But it doesn't solve this problem

Do unterstand someone this following soure?:

[https://bugs.launchpad.net/ubuntu/+source/gcj-4.5/+bug/779908](https://bugs.launchpad.net/ubuntu/+source/gcj-4.5/+bug/779908)

Maybe someone understand this soure and can show how to solve my problem.

I set also pictures in the attachments. Please take a look at these pictures

Please help to solve my problem!

Regards, Juergen

---

### Post by baumtopf on 2011-06-26
Hello Ubuntu users,

Do you understand my problems?
No ideas?
Is the problem too difficult?

Please answer!

Regards, Juergen

---

### Post by joneberger on 2012-02-23
I'm currently having the same error.  Only mine is taking place when trying to separate the pages.

Did you arrive at a solution?  I'll keep you posted if I come to a solution.

Jon

---

### Post by ledjazz on 2012-09-13
Hi there,

I am having the same issue with PDF CHAIN. The trick I use is that I work only with files located on my Desktop, and it works perfectly. The bugg may indeed be related to the string length of the file name/location (just a guess).

Hope this helps solve your problem as for me.

Ciao.
Francois

---

