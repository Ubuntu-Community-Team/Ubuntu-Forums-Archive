---
title: "How to &quot;use force_addr=0xaddr&quot;"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by Kirgothi on 2011-05-22
Hi all,    I am trying to install 11.04 on Virtual Box.  I keep getting messages about "you need to upgrade your BIOS or use force_addr=0xaddr"  I do not need to upgrade my BIOS.  So, how does one "use force_addr=0xaddr"?  What does that mean exactly?  I have been using Ubuntu for about a year and I have never run into problems like this before.  I have no idea where to start.  I have searched the forum but this always seems to produce results for different problems than I am having.  I am using a Core 2 duo, 2gig ddr2 ram, Asus board, nvidia 7950 GT  This will boot up into a gnome2 environment despite the error messages.  I am wanting to give Unity a try.  Does it even work with Nvidia cards?  I have heard bad bad things.  If I try to run Kubuntu 11.04 I get similar error messages.    Kir

---

### Post by Kirgothi on 2011-05-23
Wow.  Nobody else is having this problem eh?  Hrmm.  Well I tried, I guess I will have to use Kubuntu for the time being.  Maybe Mint 11 when it is released.

---

### Post by Toz on 2011-05-23
> **Kirgothi said:**
> Wow.  Nobody else is having this problem eh?
A simple search for force_addr in the forums search bar would have yielded some results.>   Hrmm.  Well I tried, I guess I will have to use Kubuntu for the time being.You will get the same warning message.> Maybe Mint 11 when it is released.KYO.

Google directed me to this link for a fix:```
http://finster.co.uk/2010/11/16/virtualbox-piix4_smbus-error/
```

---

### Post by Kirgothi on 2011-05-24
Let me repeat myself, a search of the forum did not produce any helpful results.  Hence you not posting any links to posts on this forum.  Maybe I wasn't clear enough, I already read those posts and the solutions there did not work.  I still get this error message.

The link you provided does mention the problem happening on Ubuntu 10.10, not 11.04.  I am willing to give the suggestion a shot, but it doesn't mention where to run the sudo commands, on the virtual installation or on the Ubuntu installation that I am running the VirtualBox on.

Please, read the response this time and don't repeat what the original post already said.

Thanks. :)

---

### Post by tgalati4 on 2011-05-24
When the kernel tries to load a module and the hardware doesn't react the way it is supposed to, you can sometimes recover by reloading the module at a specific memory address.  Sometimes you don't notice what features are missing (or not working).  The force_addr parameter is used to force the driver to load at a specific memory location.  You might not need the module at all:

In your case, there is an error loading the piix4_smbus module.

A quick google search on pii4x_smbus shows that it is a system message bus controller for the following:

[http://hardware4linux.info/component/15119/](http://hardware4linux.info/component/15119/)

Since you have an ASUS board and not an HP board (although ASUS makes boards for a lot of companies), it could be a real error or the kernel is just confused.  So either don't worry about it, or do something about it.  Put piix4_smbus in /etc/modprobe.d/blacklist and it won't get loaded in the future.  If it doesn't get loaded, you won't get errors.  If your machine works OK, then don't worry about it.  If your machine doesn't boot, crashes randomly, or catches fire, then you will have to do something about it.

"My machine caught fire.  What do I do about it?"

---

### Post by newnow on 2011-05-24
> **Kirgothi said:**
> Hi all,    I am trying to install 11.04 on Virtual Box.  I keep getting messages about "you need to upgrade your BIOS or use force_addr=0xaddr"  I do not need to upgrade my BIOS.  So, how does one "use force_addr=0xaddr"?  What does that mean exactly?  I have been using Ubuntu for about a year and I have never run into problems like this before.  I have no idea where to start.  I have searched the forum but this always seems to produce results for different problems than I am having.  I am using a Core 2 duo, 2gig ddr2 ram, Asus board, nvidia 7950 GT  This will boot up into a gnome2 environment despite the error messages.  I am wanting to give Unity a try.  Does it even work with Nvidia cards?  I have heard bad bad things.  If I try to run Kubuntu 11.04 I get similar error messages.    Kir

I encountered the similar problem with you.but one of my friend help me to solve it ,the regret is I forget to ask how he done it .tell you next time after I got the answer.

---

