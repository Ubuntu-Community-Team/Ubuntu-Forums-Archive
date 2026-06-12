---
title: "No sound with SigmaTel ID 7698"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dr.Suave on 2009-03-18
Hi

The soundcard SigmaTel ID 7698 just flat-out doesn't work at the minute with Jaunty or Intrepid.

It also doesn't work on Fedora, OpenSUSE, Linux Mint or Mandriva.

HOWEVER!

[A patch has been written]("https://qa.mandriva.com/show_bug.cgi?id=41385#c1") (first comment in link) by some folks over at Mandriva.

I'm afraid I'm too much of a newbie to even figure out how this patch is applied, but from the sounds of it, it worked quite successfully.

It would be great if this card was supported in Jackalope, as it happens to be the card put in every laptop given out by the government to disabled students in Britain.

If someone can explain to me how to install the patch, I will test it in Jackalope and Intrepid.

Thanks a lot

Wilf

(PS! Don't hesitate to ask if more information is needed!:D)

---

### Post by Taiebot65 on 2009-03-18
Have you looked at the documentation about sound?
[https://help.ubuntu.com/community/Sound]("https://help.ubuntu.com/community/Sound")

---

### Post by Dr.Suave on 2009-03-18
I'm afraid so. I've tried every tutorial I can find, and have searched for this sound card, and my brand of laptop, and the only success story I've come across is the Mandriva patch I've linked to.

Here's the post I made when I first found the card didn't work: [http://ubuntuforums.org/showthread.php?t=1086627](http://ubuntuforums.org/showthread.php?t=1086627)

---

### Post by Dr.Suave on 2009-03-18
Could anyone even be able to point me towards some documentation telling me what to do with .patch files?

---

### Post by Taiebot65 on 2009-03-18
Have you applied model=dell-d21 in your 
sudo nano /etc/modprobe.d/alsa-base

---

### Post by crimsun on 2009-03-19
> **Dr.Suave said:**
> A patch has been written[/URL] (first comment in link) by some folks over at Mandriva.

I've [added this]("http://kernel.ubuntu.com/git?p=dtchen/ubuntu-jaunty.git;a=commitdiff;h=10429374a389b18ff30a96b0c0cadb6db8809180") to my tree.

---

### Post by Dr.Suave on 2009-03-19
> **Taiebot65 said:**
> Have you applied model=dell-d21 in your 
sudo nano /etc/modprobe.d/alsa-base

I have indeed.

---

### Post by Dr.Suave on 2009-03-19
> **crimsun said:**
> I've [added this]("http://kernel.ubuntu.com/git?p=dtchen/ubuntu-jaunty.git;a=commitdiff;h=10429374a389b18ff30a96b0c0cadb6db8809180") to my tree.

Thanks! That's great!

I'll download a new jaunty build - when do you think this will appear in the builds?

---

### Post by crimsun on 2009-03-19
> **Dr.Suave said:**
> Thanks! That's great!

I'll download a new jaunty build - when do you think this will appear in the builds?

No idea. I'll need to roll a test kernel for you first.

---

### Post by crimsun on 2009-03-19
Also, are you running 32- or 64-bit?

---

### Post by Dr.Suave on 2009-03-19
Ok dokes - will wait patiently! I'm running 32 bit.

---

### Post by crimsun on 2009-03-19
Due to beta freeze going into effect shortly, the kernel is now in SRU mode, which means you need to file a bug affecting the linux source package in order for me to justify requesting a pull from my tree.

---

### Post by Dr.Suave on 2009-03-19
> **crimsun said:**
> Due to beta freeze going into effect shortly, the kernel is now in SRU mode, which means you need to file a bug affecting the linux source package in order for me to justify requesting a pull from my tree.
Ok, have done: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345631)

Hope the bug report is in the right place.

Thanks a lot!

---

### Post by crimsun on 2009-03-20
Please test the appropriate kernel at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)

---

### Post by Dr.Suave on 2009-03-20
> **crimsun said:**
> Please test the appropriate kernel at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)
Thank you so much!!!

On a fresh install of Jaunty Alpha 6, with the .deb applied I now have sound! It only comes out of my on board laptop speakers, but I'm sure with more fiddling I'll get the external speakers working too.

I'll double check with the Jaunty live disk to make sure that they wouldn't have been working without the .deb (though they certainly didn't in Intrepid), as before I applied the patch I had my speakers plugged in while I was testing.

I'll search the forums for enabling external speaker sound.

Once again, thank you so much! This kind of developer to user interaction is in my opinion one of the best things about Linux.

:KS

---

### Post by Dr.Suave on 2009-03-20
Ok, I've just checked with the original Alpha 6 kernel, and can confirm that it was definitely your .deb that enabled sound. :D

After installing the patch the codec was detected as Sigmatel STAC9205.

Have been playing with model numbers in /etc/modprobe.d/alsa-base.conf and most that I've tried (ref, dell-m42, dell-m43, dell-m44, dell-d21) all work with the on board speakers, but not the headphone jack (except the dell-m43 and ref, which don't work at all). When I use the dell-d21 setting if I plug my speakers in I'm sure I can hear them playing for a second, but then cut out.

None of the model numbers seem to give me a headphone jack switch in the volume control alsa mixer.

---

