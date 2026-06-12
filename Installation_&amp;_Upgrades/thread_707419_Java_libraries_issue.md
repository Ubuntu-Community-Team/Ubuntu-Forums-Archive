---
title: "Java libraries issue"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by zeeshan4it on 2008-02-25
Hi,

I tried to install zend php studio on gusty gibbon and it displayed me the following error:

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

'SWING' UI not supported by VM.  Reverting to AWT.
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at java.awt.Window.init(Unknown Source)
        at java.awt.Window.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Any idea what i need to install in order to setup this zend application on ubuntu gusty gibbon.

Zeeshan

---

### Post by taurus on 2008-02-25
What was the exact command that you ran and did you log in as root or **su** to root?

---

### Post by zeeshan4it on 2008-02-25
HI,

I am using this command in terminal as root:

root@ubuntu:/media/hda5/soft/zend# sudo ./ZendStudioForEclipse-6_0_0.bin

---

### Post by taurus on 2008-02-25
> **zeeshan4it said:**
> HI,

I am using this command in terminal as root:

root@ubuntu:/media/hda5/soft/zend# sudo ./ZendStudioForEclipse-6_0_0.bin

You look in as root!  Try login with your regular username and password.  Then, from a terminal, run

```
cd /media/hda5/soft/zend
sudo ./ZendStudioForEclipse-6_0_0.bin
```

---

### Post by zeeshan4it on 2008-02-25
Great!

That works now. Thanks alot.

Zeeshan

---

