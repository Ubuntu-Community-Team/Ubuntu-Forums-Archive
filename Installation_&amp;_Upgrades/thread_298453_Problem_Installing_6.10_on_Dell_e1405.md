---
title: "Problem Installing 6.10 on Dell e1405"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by papafred07 on 2006-11-12
Hi all,

I am relativley new to the linux world and am experiencing problems with the Edgy Eft 6.10 install. During installation a problem occurs that states a failure to load the X server or something to that extent. Any help will be greatly appreciated.

Thanks,
Fred

---

### Post by ReaderRat on 2006-11-12
Hello, Fred, welcome to the forums.
If you are using the Edgy 6.10 LiveCD, did you run the MD5checksum on the disc (on the boot menu) to find out if you have a "good copy"? If not, try that first. Do you have 256Megs RAM required to install Ubuntu? (or do you have 192Megs needed to install the Alternate CD?) I will check back in a while...


EDIT: I checked back....No response...

---

### Post by papafred07 on 2006-11-13
hey thanks for the reply,

sorry it took me a bit to get back.  i ran the check and came back with zero errors.  also, i have 1gb of RAM.

thanks again for the help,
Fred

---

### Post by ReaderRat on 2006-11-13
You might try to install in 'Safe Graphics Mode' (on the install menu), and set up video after install.

---

### Post by papafred07 on 2006-11-13
alright, let me give that a try

---

### Post by papafred07 on 2006-11-13
i encountered the exact same error

---

### Post by papafred07 on 2006-11-14
This is extremely frustrating. does anyone else have any ideas?

---

### Post by ZoidbergForPresident on 2006-11-14
I have the exact same problem...

It probably lies in the graphic driver (I have an ATI card and a Dell too)...

And it seems no-one has a definite answer for that problem so... I'll stay away from any Linux Distribution from now on...

Ubuntu is not more simple and easier to use than any other Linux... I'm quite disappointed...

---

### Post by ski309 on 2006-11-14
> **ZoidbergForPresident said:**
> I have the exact same problem...

It probably lies in the graphic driver (I have an ATI card and a Dell too)...

And it seems no-one has a definite answer for that problem so... I'll stay away from any Linux Distribution from now on...

Ubuntu is not more simple and easier to use than any other Linux... I'm quite disappointed...
[http://ubuntuforums.org/showthread.php?t=292299&highlight=6.10+e1405](http://ubuntuforums.org/showthread.php?t=292299&highlight=6.10+e1405)

It sucks that E1405s have this problem with Edgy installation, but hopefully with some of the features they plan on including in Feisty Fawn, such as '[bulletproof x]("https://features.launchpad.net/distros/ubuntu/+spec/bullet-proof-x")', things will change in about 6 months :P

---

### Post by ZoidbergForPresident on 2006-11-14
> **ski309 said:**
> [http://ubuntuforums.org/showthread.php?t=292299&highlight=6.10+e1405](http://ubuntuforums.org/showthread.php?t=292299&highlight=6.10+e1405)

It sucks that E1405s have this problem with Edgy installation, but hopefully with some of the features they plan on including in Feisty Fawn, such as '[bulletproof x]("https://features.launchpad.net/distros/ubuntu/+spec/bullet-proof-x")', things will change in about 6 months :PSo it's the solution? Wait 6 months? Hopefully?

Tss..

---

### Post by papafred07 on 2006-11-14
are these problems also apparent with dapper?

---

### Post by papafred07 on 2006-11-15
nobody has a solution?  it can't be unique to just this laptop.  i really was looking forward to entering into the linux world and the is a huge road block.

---

### Post by AliceOne on 2006-11-16
Hi, on my system:

- DELL Dimension 5150
- ATI X300 integrated graphic card
- 1GB Ram
- DELL 2005 TFT (16:10)

I experienced the same when trying to install Ubuntu 6.10, it's related to the graphic card/driver. I fixed it in this way:

1. Boot in 'Safe Graphics Mode'
2. When X crash, CTRL-ALT-F2
3. Edit (vi) /etc/X11/xorg.conf
4. Im my case it worked setting driver = radeon instead of ati
5. restart X (startx)

---

### Post by ski309 on 2006-11-17
> **ZoidbergForPresident said:**
> So it's the solution? Wait 6 months? Hopefully?

Tss..No, the solution can be found in the link at the beginning of my post.

---

### Post by temna on 2006-12-01
Looks like your "answer" only helps after Edgy is installed..  The only way I have been able to get Edgy installed is to install Dapper in safe mode and then do a distro update..  Oh, but this screws with the ability to get both cores running..  I have been beating my head against a wall trying to get Edgy on my e1405..  Everything was working axcept for the dual core thing, then I installed Flash in Firefox..  *sighs*  Now Firefox crashes on every Flash site..  But that is a different issue..  How do I actually install Edgy on my e1405 without installing Dapper first?

BTW, I spent a long time trying all of the "safe" modes on my Edgy disk, and none of them worked..  I got the error connecting to X error on every single mode..

---

