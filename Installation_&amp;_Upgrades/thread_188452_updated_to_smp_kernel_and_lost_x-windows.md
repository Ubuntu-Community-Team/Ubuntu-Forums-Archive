---
title: "updated to smp kernel and lost x-windows"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-06-04
I started with the default 386 uniprocessor kernel (apparently the only one present in the distribution CD). 
The initial screen resolution was poor (1024x768) and could not be upgraded.

I installed nvidia-glx and did nvidia-glx-config and dpkg-reconfigure xserver-xorg.
After all this, my nvidia gpu and big LCD monitor worked OK at high resolution.

Then I noticed I had only 1 cpu enabled, and I intalled the 686 smp kernel using synaptic. Now the x-server crashes at startup. 

I tried apt-get install nvidia-glx, but was informed it was already there. Is there no new version matching the different kernel?

How do I update the nvidia driver (and whatever else is needed) for the 686 smp kernel, while using the 386 kernel that still works?

thanks

---

### Post by tseliot on 2006-06-04
you need the restricted modules for each kernel of yours.

Boot in your new kernel
then type:
sudo apt-get install linux-restricted-modules-`uname -r`

---

### Post by kornelix on 2006-06-04
Thanks. 

Is 'uname -r' to be taken literally or is this some other name I have to supply? a package name? 

Is this a separate update system from synaptic? 

I looked for relevant docs before posting, and found nothing. Is there a relevant doc for me?

thanks again

a favorite old line: preparing a face to meet the faces that you meet.

---

### Post by tseliot on 2006-06-04
[QUOTE=kornelix]Thanks. 

Is 'uname -r' to be taken literally or is this some other name I have to supply? a package name? 

Is this a separate update system from synaptic? 

I looked for relevant docs before posting, and found nothing. Is there a relevant doc for me?

thanks again

a favorite old line: preparing a face to meet the faces that you meet.[/QUOTE]
it means that the output of the uname -r command is added to the end of sudo apt-get install linux-restricted-modules- so as to be sure that you're getting the restricted modules for the kernel you are using (i.e. the one you have booted in).

If you want you can install the restricted modules from Synaptic by booting in your old kernel.

---

### Post by kornelix on 2006-06-04
[QUOTE=tseliot]it means that the output of the uname -r command is added to the end of sudo apt-get install linux-restricted-modules- so as to be sure that you're getting the restricted modules for the kernel you are using (i.e. the one you have booted in).[/QUOTE]

OK, I got it.  thanks. 

[~] $ echo $(uname -r)
2.6.15-23-386
[~] $

---

### Post by kornelix on 2006-06-04
[QUOTE=tseliot]it means that the output of the uname -r command is added to the end of sudo apt-get install linux-restricted-modules- so as to be sure that you're getting the restricted modules for the kernel you are using (i.e. the one you have booted in).

If you want you can install the restricted modules from Synaptic by booting in your old kernel.[/QUOTE]

Using synaptic with the old kernel (386 uniprocessor) pulls in the modules for that kernel.

I booted to the 686 recovery system and tried
    # apt-get install linux-restricted-modules-'uname -r'
and other variations like `uname -r´ but the command interpreter
refused to resolve what was inside the quotes, and apt-get looked
for a module named "... uname -r".

So I used  
   # apt-get install linux-restricted-modules-2.6.15-23-686
and this worked.

I rebooted and the x-server worked and both CPUs are working.
Thanks for your help.

---

### Post by tseliot on 2006-06-04
[QUOTE=kornelix]Using synaptic with the old kernel (386 uniprocessor) pulls in the modules for that kernel.

I booted to the 686 recovery system and tried
    # apt-get install linux-restricted-modules-'uname -r'
and other variations like `uname -r´ but the command interpreter
refused to resolve what was inside the quotes, and apt-get looked
for a module named "... uname -r".[/QUOTE]
The right apostrophe is ` and it's `uname -r`

OR, if you don't like apostrophes you can try with apt-get install linux-restricted-modules-$(uname -r)

---

### Post by CrunchyDoodle on 2006-06-11
I had a similar problem trying to use the 686 kernel and this thread gave me the `secret handshake` I needed to get it going.

Bye.    :cool:

---

### Post by kornelix on 2006-06-11
The Italo-british poet does good work.

---

### Post by tseliot on 2006-06-11
[QUOTE=kornelix]The Italo-british poet does good work.[/QUOTE]
LOL

---

