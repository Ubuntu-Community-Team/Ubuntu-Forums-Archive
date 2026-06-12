---
title: "Any idea about the following error message when &quot;Finished Installation&quot;?!"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-05-28
Hi Folks!:popcorn:

Do anyone has an idea on what could be the probable cause of the following error message, I encountered after the installation of 10.04LTS?!

[2038.66382] end_request:I/O error, dev sr0, sector 505488:confused:

The above line hijacked the screen in multiple Nos., Disk came out(quite natural when 100% installation gets done!).

Pressing ENTER, says-* will now Restart.:guitar:

& Done!

---

### Post by ibuclaw on 2010-05-28
> **Saurabhdua said:**
> I encountered after the installation of 10.04LTS?!

[2038.66382] end_request:I/O error, dev sr0, sector 505488:confused:


sr0 is non-human readable name for the CD-ROM device in Linux.

It probably means that an application was still trying to read the Disk when it got ejected. Nothing major. Your system should be OK. ;)


Although you can't rule out the possibility that the CD you burned is bad. If you find yourself having system issues after reboot, could trying burnin ghte iso onto a CD again, but at a **slower** speed.

Regards
Iain

---

### Post by Saurabhdua on 2010-05-28
Hello Iain!

What kind of system issues one can encounter owing to this flaw?I was facing a shaking screen trouble before this 2nd attempt to install Ubuntu 10.04!

First attempt did cause very much the same thing with only difference being, that this time I waited patiently & pressed ENTER instead of giving my machine a FORCED MANUAL shutdown.

Secondly, I didn't burn any disc BUT I have got it shipped FREE through Ubuntu shipit.

---

### Post by ibuclaw on 2010-05-28
> **Saurabhdua said:**
> Hello Iain!

What kind of system issues one can encounter owing to this flaw?I was facing a shaking screen trouble before this 2nd attempt to install Ubuntu 10.04!

First attempt did cause very much the same thing with only difference being, that this time I waited patiently & pressed ENTER instead of giving my machine a FORCED MANUAL shutdown.

Secondly, I didn't burn any disc BUT I have got it shipped FREE through Ubuntu shipit.

OK, I'll assume that the CD you got is bad then. When you boot from the CD, the initial screen should have a "Check CD for Defects" option. Select that and report what it comes back with.

Regards

---

### Post by ajgreeny on 2010-05-28
I think with 10.04 you need to keep tapping any key when the CD boots to get to the menu with the options for checking the CD etc etc.

If you don't hit a key, it just starts booting to the live CD desktop.

---

### Post by Saurabhdua on 2010-05-29
Ajgreeny is absolutely right!

I don see any option like past Ubuntu instances where it use to pop up choices like install,try & check CD for defects.Straightaway it takes me to the Desktop to experience the Demo.

So Ajgreen, what KEY do I need to tap on boot?

---

### Post by ibuclaw on 2010-05-29
> **Saurabhdua said:**
> Ajgreeny is absolutely right!

I don see any option like past Ubuntu instances where it use to pop up choices like install,try & check CD for defects.Straightaway it takes me to the Desktop to experience the Demo.

So Ajgreen, what KEY do I need to tap on boot?

Any key will do.

ie: Escape.

---

### Post by kansasnoob on 2010-05-29
That's a known issue and it's in the release notes:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install)

> I/O error after CD is ejected at end of install

In some cases, ejecting the CD at the end of installation will leave errors on the screen such as:

end_request: I/O error, dev sr0, sector 437628

these error messages indicate that the system is still trying to access some files on the CD, and are harmless except that they obscure the message asking the user to **press Enter to reboot**. You can safely remove the CD from the tray and press Enter at this point to reboot to your new Ubuntu system. (539027) 

---

### Post by Saurabhdua on 2010-05-31
OK..if that's a known issue then 'Checking CD for Defects' won't do any good!

But then what's causing this 'Shaking Screen' trouble, is this a known issue as well? Somehow, either Ubuntu or my Graphics Card are finding it hard to gel together!

Are there any known issues with "Screen Resolution" & Ubuntu 10.04?

---

