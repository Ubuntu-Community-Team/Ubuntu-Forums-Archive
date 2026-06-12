---
title: "Updated ubuntu and now I am in a login loop"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by tod-lazarov on 2015-08-18
I recently installed Ubuntu and it was working fine while logging in at least a dozen times. I switched the GPU drivers from the default one to proprietary, they got installed, a couple of minutes later an updated popped up, it installed and it asked to restart the computer. 

After the restart I type in my password, it goes black, makes that login sound and it goes back to the screen asking me for my password. Same with the guest session. Ctrl + alt + F1 goes to a black screen where I cant see or do anything.

---

### Post by Bashing-om on 2015-08-18
tod-lazarov; hello;

As :
> 
 I switched the GPU drivers from the default one to proprietary, 

And the problem became evident after a system update; We can surmise that the update broke the proprietary graphics driver.

The question now is how did you install the proprietary driver ? Knowing this we can try to purge the proprietary graphics driver and properly install a driver .

Presently, in order to proceed; can you boot to recovery mode from the grub boot menu ?
Also, we need to know what release you are running, and what the Desktop Environment is, unity or other(s)  ?

[INDENT][INDENT]we do fault isolation
[INDENT][INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-08-18
Are you running 15.04?
If so it seems you are not alone, and it appears to be possibly the AMD fglrx driver that is causing the problem; see [http://ubuntuforums.org/showthread.php?t=2291217&p=13340683#post13340683](http://ubuntuforums.org/showthread.php?t=2291217&p=13340683#post13340683) for a similar situation.

I can not help you more than this, I'm afraid, as I have not used any AMD graphics for a very long time, but if you remove all fglrx packages and then search out how to get the right resolution, if that becomes a problem for you, you may manage to avoid this login loop but still get a GUI desktop.

---

### Post by QIII on 2015-08-18
If this is what I think it is, then the problem is not the fglrx driver itself.  That is a symptom.  For many, this is being caused by an error in the package to upgrade the kernel to 3.19.0.26.  Because of that error, the fglrx module can not be built properly.  There are at least 3 reported bugs regarding this on Launchpad.

I have not had time to confirm for myself, but 3.19.0.27 is apparently in the -proposed repo and works properly.  But unless you know how to enable the -proposed repo and pin packages so you don't get a flood of other proposed packages you don't want, that isn't of much help to the normal user.

This issue will not be "fixed" until the new kernel package is in the main repo and has been confirmed to work

Best bet for now, if you ask me, is to boot kernel 3.19.0.25 from GRUB by arrowing down to "Advanced options" and then arrowing down to the 3.19.0.25 kernel.

---

### Post by tod-lazarov on 2015-08-19
> **ajgreeny said:**
> Are you running 15.04?
If so it seems you are not alone, and it appears to be possibly the AMD fglrx driver that is causing the problem; see [http://ubuntuforums.org/showthread.php?t=2291217&p=13340683#post13340683](http://ubuntuforums.org/showthread.php?t=2291217&p=13340683#post13340683) for a similar situation.

I can not help you more than this, I'm afraid, as I have not used any AMD graphics for a very long time, but if you remove all fglrx packages and then search out how to get the right resolution, if that becomes a problem for you, you may manage to avoid this login loop but still get a GUI desktop.

Yes and Yes. I thought this might not be a specific problem to my computer. I'll take a look at that thread and see if I can fix it. Thank you for the prompt response.

---

### Post by tod-lazarov on 2015-08-19
Ok this does not work for me. Trying ctrl + alt + any of the f buttons goes into a black screen that I have to restart out of. Also running 3.19.0.25 does the exact same thing, login loop. Any other ideas guys?

---

### Post by legoclone09 on 2015-08-19
I get this with Nvidia graphics for AMD x86, but I can use ctrl+alt+f keys.cI did the update yesterday as well.

---

