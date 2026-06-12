---
title: "Ubuntu 10.10 Netbook Edition installer just freezes when I try to install/live run"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by shlstrm on 2011-02-17
Hi peoples, I've googled to my best capabilities but haven't found anything that resembles this problem. :(

I'm booting Ubuntu 10.10 Netbook Edition from USB on an ASUS Eee 1018P. Everything works just fine, but when the graphical installer pops up and gives me the opportunity to choose from live try or install it just freezes up on me, whichever option I try. Yes, I've been patient and waited for 4-5 mins. :)

On a side note, it doesn't show any wireless network interfaces either. Don't know if this is a problem.

When I try the 10.10 Desktop edition the live image works just fine, with the exception of no wifi and no sound. It did suggest a proprietary driver for wifi, so that is probably just a minor caveat. As for sound I guess google is my friend.

However, I'd rather just install UNE instead of installing Desktop and then start removing packages and installing the UNE packages etc etc...

Is there anyone else with this problem or a similar one? Is there a way to pull up a terminal so I can check some logs and which one except for dmesg is most interesting?

Sorry for long post. :)
Cheers!

---

### Post by corncob on 2011-02-17
It could be a bad download or write to the pen drive.  Try to download it again or run an MD5sum:
[https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file](https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file)

---

### Post by Dumb_Fred on 2011-02-25
I have been trying to solve this problem and finall have a solution. After tapping live cd option it just hangs forever. I go up the top to the install with a red symbol on the left. Select the red button which says want to quit select quit and it loads up the live CD. This works for my ASUS netbook.

---

### Post by Dumb_Fred on 2011-02-25
> **Dumb_Fred said:**
> I have been trying to solve this problem and finall have a solution. After tapping live cd option it just hangs forever. I go up the top to the install with a red symbol on the left. Select the red button which says want to quit select quit and it loads up the live CD. This works for my ASUS netbook.

Confirmed another solution - go and have a cup of coffee when the options are displayed and come back and make your choice. I saw somewhere else that you have to wait 4.5 minutes!!!

---

### Post by simonedge on 2011-02-28
> **Dumb_Fred said:**
> Confirmed another solution - go and have a cup of coffee when the options are displayed and come back and make your choice. I saw somewhere else that you have to wait 4.5 minutes!!!
It's about a minute on a fairly fresh install - click 'try', wait; screen cuts to black, with a message about something failing 'due to unknown user ID (0)', then (back) to the desktop where it asks me to unlock the keyring.

This is on a Dell Mini 1012, booting from an SD card.

---

