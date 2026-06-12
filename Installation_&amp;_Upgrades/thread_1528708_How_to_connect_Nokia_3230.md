---
title: "How to connect Nokia 3230"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by srikrishnan on 2010-07-11
Hi All,

I have Ubuntu 10.04 LTS in my system. I want to connect my Nokia 3230 in my Ubunty OS. But it was not recognizing it. Even I have tried to install Nokia PC suite using Wine. I think exe was not supported by Wine, it will not run the exe.

Can anybody have any idea whether it is possible or not? I am very beginner to Linux. So please help me.

Thanks in Advance,
Srikrishnan

---

### Post by labinnsw on 2010-07-12
I was able to get a 3220 connected using Wammu (gammu). This only allowed me to access messages.

Still trying to get gnokii (or Xgnokii), gMobileMedia, and ObexFTP front-end to work. ObexFTP front-end looks like the most promising.

I am hoping that I will be able to figure out one or more of these and that if I do, I will be able to pass data to and from the phone.

These are all applications available in Ubuntu Software center. My interest is mainly to transfer images.

Please post your links or solutions if you figure it out before I do. I don't believe the links I have found so far are worth posting. They haven't helped me much so far.

---

### Post by thahir1986 on 2010-07-12
U can connect nokia phones (any other mobile phones having bluetooth) using bluetooth port. 

It's easy man....

---

### Post by labinnsw on 2010-07-12
I would like to connect using usb cable CA-42.

I have found [a link that I think is worth posting]("http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml")

Now here are my problems.

1. lsusb does not list any nokia connection. By pluging in and pluging out, I have drawn the conclusion that it is listed as Dazzle.```
Bus 008 Device 002: ID 07d0:4101 Dazzle
```

2. Lucid has no 040-permissions.rules or any permissions.rules for that matter. If it does, I have been unable to find it.

3. Other rules referring to usb contain a different syntax from what is described in the solution.

4. The Read Me in /etc/udev/rules.d says you can add rules but does not indicate how to edit rules.

Just an aside,
5. Adding rules (40-permissions.rules and 65-persistent-storage.rules) messes up the auto mounting of my partitions.

---

### Post by labinnsw on 2010-07-12
> **srikrishnan said:**
> I think exe was not supported by Wine, it will not run the exe.

Right click on the .exe file, and under the Permissions tab make it executable.

Installing Nokia PC suite did not work for me but that does not mean it won't work for you.

---

### Post by srikrishnan on 2010-07-14
Hi,

Thanks for your suggestion.

If I succeed, let you know

Thanks,
Srikrishnan

---

### Post by labinnsw on 2010-07-14
Can anyone tell me where to find the source code that would generate this error?

```
labinnsw@UbuntuLTS-desktop:~$ /usr/bin/obexftp-frontend
2010-07-14 22:49:06,583 INFO 	 [AWT-EventQueue-0    ] Loaded the configuration from the disk (at ConfigurationDialogHelper:237)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at org.jvnet.substance.SubstanceSpinnerUI$3$2.run(SubstanceSpinnerUI.java:284)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
```

Is this it? If it is, can you help me to figure out what the problem is?

---

### Post by labinnsw on 2010-07-16
Bump!

---

### Post by labinnsw on 2010-07-17
[So it appears Obex won't work for me.]("http://sensi.org/~ak/openobex-usb/")

---

### Post by labinnsw on 2010-07-17
[Looks like the problem might be partially solved by using a genuine Nokia CA-42 cable with Wammu. It seems also that photos cannot be viewed or transferred.]("https://answers.launchpad.net/ubuntu/+question/3695")

---

### Post by yugajisu on 2011-08-15
> **srikrishnan said:**
> Hi All,

I have Ubuntu 10.04 LTS in my system. I want to connect my Nokia 3230 in my Ubunty OS. But it was not recognizing it. Even I have tried to install Nokia PC suite using Wine. I think exe was not supported by Wine, it will not run the exe.

Can anybody have any idea whether it is possible or not? I am very beginner to Linux. So please help me.

Thanks in Advance,
Srikrishnan
where can i get nokia pc suite, or how can i use my phone to transfer file?

---

