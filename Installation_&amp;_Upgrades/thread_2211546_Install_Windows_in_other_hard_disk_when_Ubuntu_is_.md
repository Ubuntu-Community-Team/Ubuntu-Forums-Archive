---
title: "Install Windows in other hard disk when Ubuntu is Booted"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by mirkos90 on 2014-03-16
Hi, for my own curiosity I would like to ask a question :)
So simple: I own two hard drives of which one is installed in Ubuntu and it's booted, now I would like to install Windows in the second hard drive.
Can I do this installation without restarting the computer and boot an pendrive/cd?
Obviously I do not mean solutions such as Virtual Box or clones of Wubi
Thank you
Mirko

---

### Post by ajgreeny on 2014-03-16
Not possible as far as I'm aware.

---

### Post by mirkos90 on 2014-03-17
Why that's impossible?
Mirko

---

### Post by ajgreeny on 2014-03-17
> **mirkos90 said:**
> Why that's impossible?
Mirko
Because other than virtualisation there is no method available from anywhere to install windows on a machine while ubuntu is still running on that same machine.

You have to shutdown Ubuntu then boot to the install medium of windows in order to install it.  There is no other way.

---

### Post by mastablasta on 2014-03-17
maybe only a pirated copy, but you would have to setup all files manually and flag them correctly.

or maybe with an OEM image -  you would just put/extract whatever... the image on the other disk

---

### Post by mirkos90 on 2014-03-17
Nice, so, can i install windows on a virtual machine and copy all files in a new hard disk?
With this operation can be error with hardware/driver on windows installation?
Thank you!
Mirko

---

### Post by ajgreeny on 2014-03-17
> **mirkos90 said:**
> Nice, so, can i install windows on a virtual machine and copy all files in a new hard disk?
With this operation can be error with hardware/driver on windows installation?
Thank you!
Mirko
Not sure exactly what you're asking here.

You can certainly install windows in a VM, and then, with appropriate folder sharing, you can use that VM to copy files to and from itself to another OS or disk.

In a VM hardware drivers are not relevant as the VM uses the virtualised hardware of the host, so if your host OS runs well and has sufficient resources for VMs, the guest will also run well.

---

### Post by Mark Phelps on 2014-03-17
In your original post you said: > Obviously I do not mean solutions such as Virtual Box 

So, since you're asking about a VM now, that means you've reconsidered?

You most likely will have to activate the Windows install after you move it, even if you did so inside of Virtualbox -- because the hardware does not look the same.

Some folks who tried switching between a VM installation and a native installation discovered each time they rebooted, they would have to reactivate Windows -- and eventually, it won't let you reactivate anymore.

---

### Post by mirkos90 on 2014-03-18
> **Mark Phelps said:**
> In your original post you said: 

So, since you're asking about a VM now, that means you've reconsidered?

Well I did not mean I wanted to install Windows in VirtualBox, that's all :)
To reactivate you mean on a technical level or the "license" level?

> **Mark Phelps said:**
> 
[COLOR=#000000]discovered each time they rebooted
[/COLOR]
BSOD?
Mirko

---

### Post by Mark Phelps on 2014-03-18
> To reactivate you mean on a technical level or the "license" level?

On a license level -- because the "hash code" that MS uses to activate a copy of the OS is actually different between a native install and a VM install -- on the same hardware.  So, every time they switched, to MS, that meant they were trying to run Windows on different hardware.

> BSOD?No -- simply a prompt indicating that they needed to activate the OS.

---

