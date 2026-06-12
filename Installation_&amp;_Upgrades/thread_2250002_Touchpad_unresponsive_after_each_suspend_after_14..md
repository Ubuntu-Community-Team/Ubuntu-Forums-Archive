---
title: "Touchpad unresponsive after each suspend after 14.10 upgrade"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by user1397 on 2014-10-26
Just upgraded to 14.10 from 14.04 through the software updater tool.  No hiccups during the upgrade, but I noticed that now when I suspend and resume, my touchpad becomes unresponsive unless I restart.  My external USB mouse works fine either way, just the touchpad does not work.  I have an acer aspire E5-571 (link [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834314539")).

Any thoughts?

---

### Post by reidswan101 on 2014-10-26
Hi there, 
I'm having similar problems (on the same laptop). Unfortunately, I don't have access to my laptop at present, but I found [this]("https://help.ubuntu.com/community/SynapticsTouchpad"). I'm going to try it out as soon as I get home. The part which I think is of most interest: 
> **Touchpad not working after login**

[COLOR=#333333][FONT=Ubuntu]This usually happens when you disable your touchpad and then suspend your computer. To fix this just run this command:[/FONT][/COLOR]
```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
[COLOR=#333333][FONT=Ubuntu]If nothing else works, please see [the official Ubuntu touchpad debugging article]("https://wiki.ubuntu.com/DebuggingTouchpadDetection").[/FONT][/COLOR]


I hope this helps!

---

### Post by user1397 on 2014-10-26
> **reidswan101 said:**
> Hi there, 
I'm having similar problems (on the same laptop). Unfortunately, I don't have access to my laptop at present, but I found [this]("https://help.ubuntu.com/community/SynapticsTouchpad"). I'm going to try it out as soon as I get home. The part which I think is of most interest: 


I hope this helps!
Ah, thank you for the reply.  Unfortunately, I think this only works if you manually disable the touchpad prior to suspend, with the common Fn + F7 on most laptops.  

I tried that command to no avail in my case.  I guess we gotta keep trying!

---

### Post by Javier_Garca on 2014-10-28
Hello,
same problem here :/ I have an Acer Aspire E5-471 with Elantech touchpad and happends exactly the same, everything works fine until I suspend and resume the touchpad totally dies. I have no idea how to solve but if I can help in something like posting more info tell me, i'll keep searching anyway.

---

### Post by user1397 on 2014-10-28
For now I've downgraded back to 14.04 as this is quite an annoying problem for me (I suspend and resume my laptop all the time) but if someone can figure this out I'd very much like to mark this thread as solved :)

---

### Post by BoDlulu on 2014-11-16
I have open a bug for this:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1393079](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1393079)

Please check "this bug affects you", or contribute any useful info to increase the chances of it being looked at :)

---

### Post by user1397 on 2014-11-19
> **BoDlulu said:**
> I have open a bug for this:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1393079](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1393079)

Please check "this bug affects you", or contribute any useful info to increase the chances of it being looked at :)
Awesome, thank you.

---

### Post by peddanet on 2015-01-25
Did anybody find a good solution or workaround for this annoying issue? I have of course tipped the "beeing affected" button in launchpad, but there are only 9 people beeing affected, can this be???

---

### Post by mitya-2 on 2015-01-30
I've just tried the script mentioned here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1393079/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1393079/comments/7)  (copied below) with a positive result.

This is what I did to fix this for me:

# sudo touch /etc/pm/sleep.d/10_touchpad
# sudo chmod 755 /etc/pm/sleep.d/10_touchpad

Then edit the file 10_touchpad and paste the following into it:
```

#!/bin/sh
case "${1}" in
        resume|thaw)
                rmmod hid_multitouch
                modprobe hid_multitouch
                ;;
esac
```

---

### Post by MIke_Ashby on 2015-06-20
[**[COLOR=#000000]mitya-2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1863916")'s suggestion worked on my Lenovo Yoga. I tested it several times. The mouse and trackpad click events are now working after resume from suspend. 
Thank you very much.

---

