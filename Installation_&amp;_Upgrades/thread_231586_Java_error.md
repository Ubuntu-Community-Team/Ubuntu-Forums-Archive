---
title: "Java error"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by smoothcne on 2006-08-07
Please forgive the thread, but I'm trying to run an application for my work that keeps bombing out after I recenly rebuilt and updated my system to all of the latest updates.

I'm running Dapper 6.06, Kernel is 2.6.15-26-386, and i'm running
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

Here is the message that I'm getting after invoking the application and logging into it. The Vendor won't support it any longer and I love the way it was running on my system before and now I can't get it to work:

Invocation of this Java Application has caused an InvocationTargetException. Thi s application will now exit. (LAX)

Stack Trace:
java.lang.NullPointerException
        at com.eScription.emon.XMLTable.initColumnSizes(XMLTable.java:444)
        at com.eScription.emon.XMLTable.fill(XMLTable.java:166)
        at com.eScription.emon.XMLTable.fill(XMLTable.java:130)
        at com.eScription.emon.TranscriptionistItemSelector.refresh(Transcriptio nistItemSelector.java:311)
        at com.eScription.emon.TranscriptionistItemSelector.<init>(Transcription istItemSelector.java:239)
        at com.eScription.emon.TranscriptionistFactory.<init>(TranscriptionistFa ctory.java:40)
        at com.eScription.emon.EMonToolkit.createFactories(EMonToolkit.java:134)
        at com.eScription.emon.EMon.createUI(EMon.java:316)
        at com.eScription.emon.EMon.main(EMon.java:270)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl. java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.zerog.lax.LAX.launch(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)

I have seen a ton of messages about the java.lang.NullPointerException issue but non of them explain really a good plan to fix it. Any ideas from anyone would really help. Thanks. 
](*,) :confused:

---

### Post by themusicwave on 2006-08-07
Generally you will get a null pointer exception when you don't initilize an object before you use it.  Also, if you set somethign to null and then try to use it afterwards you will get a null pointer exception.

  Something I often do to find them is take a look at everywhere I create and object and make sure it is being initilized before it is being used.

Also, put tracing code in yourprogram to output what functions it is entering.  Then once you find the piece of code with the bug try printing out objects and seeing which returns null.  

Try to think of which areas you've edited since the error began to occur.

As for all the stuff below the null pointer error, it usually will go away when you fix the null pointer bug.

Edit:  I thought you were talking about a program you wrote...I  have no idea how to fix the error if it is a vendor's software.

---

