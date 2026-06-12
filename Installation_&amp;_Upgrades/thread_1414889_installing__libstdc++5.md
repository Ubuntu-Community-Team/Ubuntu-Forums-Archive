---
title: "installing  libstdc++5"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by programmer_007 on 2010-02-24
Hi all, 

i am running a java code under eclipse in ubantu. On run i get error :
```

Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/sandeep/temp_work/tempo/lib/libAspriseOCR.so: libstdc++.so.5: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1778)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1703)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1028)
	at com.asprise.util.ocr.OCR.loadLibrary(OCR.java:247)
	at com.asprise.util.ocr.OCR.<init>(OCR.java:56)
	at Hi.main(Hi.java:25)
```

ANd to install libstdc++  i did this :
```

sandeep@training-pc1:~$ sudo apt-get install libstdc++5

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
sandeep@training-pc1:~$ 




```

Suggest me  m waiting .. wht to do now? i think i need to download it .. then from where ?:confused:

---

### Post by programmer_007 on 2010-02-24
downloaded it from 



[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download")

Binggoo  Problem solved ..

---

