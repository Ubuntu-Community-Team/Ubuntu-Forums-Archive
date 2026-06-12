---
title: "Upgraded to 12.04, now no network"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by tonymoloney on 2012-05-27
I have just done an on-line upgrade from 11.10 to 12.04 and now after the many hours it took, I have no Internet access. In fact, when I look at network settings, there is no etho and when I try to add a connection, I can't even type in the new box.

My system is a Lenovo laptop which has been running Ubuntu from the 9 series and has always been upgraded on-line without any problems.

I'm writing this on my old Lenovo running an even older Ubuntu, but it still works!

---

### Post by carl4926 on 2012-05-27
I suggest you download the 12.04 CD and see if everything works from the Live Desktop
Then consider if a new install might have been better advised than a 'upgrade'

---

### Post by HalfNote5 on 2012-05-28
What model of Lenovo (more specifically, what's the model of the network card?) 

If it's a missing driver, you can probably put it on a USB drive and install it manually.

I had to load up a couple extra drivers to make all the wifi/ethernet in the office work properly, on some machines (mostly Realtek cards).

---

### Post by tonymoloney on 2012-05-28
According to System Profiler my Ethernet Controller is a Realtek Semiconductor RTL8111/8168B PCI Express Gigabit Ethernet controller. and when I ping 127.0.0.1, I get typically less than 1ms response time, so the card is working.

Now, How do I go about downloading and installing new drivers for that card, please?

My laptop (and O/S) is a 64 bit system,, other specs on my signature.

---

### Post by carl4926 on 2012-05-28
I'm pretty sure it should just work.
Like I said. Does it work from a live CD?

Post result of
```
lspci -nnk | grep -iA2 net
```

---

### Post by tonymoloney on 2012-05-29
Thanks carl4926

I can't tell you if it works from a live CD because doing the on-line upgrade already exceeded my download limit for the month (I'm in Western Australia, not South Korea!).

However here's the output you requested. I had to run it on the non-performing laptop then copy it to a thumb drive so I could transfer it onto this working system.

And - no! it "just doesn't work".

tony@tony-laptop:~$ lspci -nnk | grep -iA2 net 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
	Subsystem: Lenovo Device [17aa:21e2] 
	Kernel driver in use: r8169 
-- 
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01) 
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195] 
	Kernel driver in use: rtl8192ce 
tony@tony-laptop:~$ ****

---

### Post by carl4926 on 2012-05-29
It looks OK, drivers in place
Is the wireless light on?
Do you see access points?

---

### Post by HalfNote5 on 2012-05-29
Okay, I know it's for Debian, but here's the package that worked for me on these models of cards:

[http://ftp.jp.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-realtek_0.28+squeeze1_all.deb](http://ftp.jp.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-realtek_0.28+squeeze1_all.deb)

Download it from another computer, save it to a flash drive or disc, and then copy it to your home directory on the new computer.

Then, run:

sudo dpkg -i firmware-realtek_0.28+squeeze1_all.deb

And it should fix the problem. At least, it has for me on three or four different computers with that particular model of card.

---

### Post by tonymoloney on 2012-05-29
Thanks for that.
It's 9:00am here in Perth and I've only just seen your advice.
I've downloaded the deb and I'll try it later on today - I'm just off to a specialist.

---

### Post by tonymoloney on 2012-05-30
OK! Thanks for your help so far. I'm back from the specialist and have followed your instructions.

Here's the output:

tony@tony-laptop:~$ sudo dpkg -i firmware-realtek_0.28+squeeze1_all.deb 
sudo: unable to resolve host tony-laptop 
[sudo] password for tony: 
Selecting previously unselected package firmware-realtek. 
(Reading database ... 422032 files and directories currently installed.) 
Unpacking firmware-realtek (from firmware-realtek_0.28+squeeze1_all.deb) ... 
dpkg: error processing firmware-realtek_0.28+squeeze1_all.deb (--install): 
 trying to overwrite '/lib/firmware/RTL8192E/main.img', which is also in package linux-firmware 1.79 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 firmware-realtek_0.28+squeeze1_all.deb 
tony@tony-laptop:~$ 

That's got me stumped, so where do I go from here?

I'm afraid that being in different time zones is going to make this a slow process.

---

### Post by HalfNote5 on 2012-05-30
Oh wow.  Yeah, that's a bit different than what I usually see.

Looks like you may have a hosts problem. 

Check out this thread

[http://ubuntuforums.org/showthread.php?t=1754106&page=3](http://ubuntuforums.org/showthread.php?t=1754106&page=3)

(the link lands you on page three, which has the most probable solution, but you might also back up and read the whole thing, if that doesn't work).

Also, if you get the hosts thing solved, and it still doesn't work, you might try that driver again, but it looks like there's (probably) a suitable one installed already.

As to the time zone observation, that's what's wonderful **and** annoying about the internet.  You can talk to people from anywhere you want, as long as you want to do so at 3 A.M.  ; )

---

### Post by tonymoloney on 2012-05-31
OK. I've checkd out that link, but it didn't help me.
I've now followed the advice given by carl4926 and it does indeed work. In fact, I'm now following this thread via the live CD.
Here's a thought - if I installed a dual boot system using this live CD, would I be able to transfer my files etc. from the failed install to the new one? Just a thought, and I'd probably be better copying my stuff to a DVD, which I could do anyhow.

---

### Post by Sef on 2012-05-31
>  I installed a dual boot system using this live CD, would I be able to transfer my files etc. from the failed install to the new one? 

Yes.

> I'd probably be better copying my stuff to a DVD, which I could do anyhow.

Or back up with [clonezilla]("http://clonezilla.org").

---

### Post by carl4926 on 2012-05-31
You could try copying the directory /lib/firmware/
From the live session

Then in your install rename /lib/firmware and replace the the firmware folder you copied from the life cd session
It's a bit tricky, but worth a shot

---

### Post by tonymoloney on 2012-05-31
I have Clonezilla, but I've never actually used it.
Question - does it clone the whole disk or can I select individual folders? I don't want to copy a bad installation and have it over write my good one.

---

### Post by carl4926 on 2012-05-31
You can clone partitions or whole drives

dd can do the same

I just never bother with that though. I keep a backup of all my important data and settings. A new install + 2hrs and I'm back to work

---

### Post by tonymoloney on 2012-05-31
OK guys. Thanks for the advice.

I'm goping to try the various options, so I'll be off the air for a while - maybe even a couple of days due to other commitments.

I'll report back when I have a result

---

### Post by HalfNote5 on 2012-05-31
> **tonymoloney said:**
> OK guys. Thanks for the advice.

I'm goping to try the various options, so I'll be off the air for a while - maybe even a couple of days due to other commitments.

I'll report back when I have a result

Good luck! Let us know how you fare.  = )

---

### Post by tonymoloney on 2012-06-02
Thanks for all the help.

I've now bitten the bullet and done a new install from the ISO.

That left me with a host of problems which I've just about sorted out.

e.g. I've had to recover all my data from my backup DVDs as trying to recover from Deja Dup and Ubuntu One got me nowhere.

I find I've now got Thunderbird instead of Evolution, which I was using and I'm having trouble importing my saved contacts.
I've had to download and re-install the Gnome Desktop Environment that I had become very happy with (as opposed to Unity)

I can't understand all those duplicity files in Ubuntu One

But apart from that, I'm back on my good Lenovo laptop and working OK

---

