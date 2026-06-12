---
title: "After Power Failure, Ubuntu wont boot past grub menu"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by swg1cor14 on 2011-10-06
We had a power failure a week ago and my Ubuntu Server 11 used to boot right into Ubuntu without any user interaction needed. After power came back on it boots to the Grub loader screen where it forces me to manually choose an option.

I hooked up a keyboard and chose one. I decided to reformat it at that point due to some changes I was making. So after a fresh reinstall of Ubuntu everything was back to working great.

Then just last night we had another power failure (which is really unusual) and when I turned my machine back on....it would sit at that grub loader screen again waiting for me to choose an option. Is there a reason? or a way to fix without having to reformat and reinstall Ubuntu?

BTW the power failures had been to the power company moving power poles because of the expanding of the roads. So its not like random unexpected power outages and shouldnt happen again.

---

### Post by Quackers on 2011-10-06
Have a look at post #2 in this thread

[http://ubuntuforums.org/showthread.php?t=1504955](http://ubuntuforums.org/showthread.php?t=1504955)

---

### Post by collisionystm on 2011-10-06
> **swg1cor14 said:**
> We had a power failure a week ago and my Ubuntu Server 11 used to boot right into Ubuntu without any user interaction needed. After power came back on it boots to the Grub loader screen where it forces me to manually choose an option.

I hooked up a keyboard and chose one. I decided to reformat it at that point due to some changes I was making. So after a fresh reinstall of Ubuntu everything was back to working great.

Then just last night we had another power failure (which is really unusual) and when I turned my machine back on....it would sit at that grub loader screen again waiting for me to choose an option. Is there a reason? or a way to fix without having to reformat and reinstall Ubuntu?

BTW the power failures had been to the power company moving power poles because of the expanding of the roads. So its not like random unexpected power outages and shouldnt happen again.


Buy a battery backup! You can integrate an APC into Ubuntu so the system will shut itself down when its notices its on battery power.

---

### Post by kelt123 on 2012-03-05
Hey, I got exactly the same problem!
Does anybody have a solution?

The problem is that after a power failure I'm forced to go to my server, connect a keyboard and press enter to pass the grub menu. Everything works fine after that. How can I get rid of this? How can I make Ubuntu to automatically continue to boot without asking my to press enter?


> **swg1cor14 said:**
> We had a power failure a week ago and my Ubuntu Server 11 used to boot right into Ubuntu without any user interaction needed. After power came back on it boots to the Grub loader screen where it forces me to manually choose an option.

I hooked up a keyboard and chose one. I decided to reformat it at that point due to some changes I was making. So after a fresh reinstall of Ubuntu everything was back to working great.

Then just last night we had another power failure (which is really unusual) and when I turned my machine back on....it would sit at that grub loader screen again waiting for me to choose an option. Is there a reason? or a way to fix without having to reformat and reinstall Ubuntu?

BTW the power failures had been to the power company moving power poles because of the expanding of the roads. So its not like random unexpected power outages and shouldnt happen again.

---

### Post by winckler on 2012-03-17
Take a look at: [https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode](https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode)

```

--- 00_header.orig      2012-03-17 01:51:43.317425938 -0300
+++ 00_header   2012-03-17 01:47:22.352131896 -0300
@@ -233,7 +233,7 @@
 {
     cat << EOF
 if [ "\${recordfail}" = 1 ]; then
-  set timeout=-1
+  set timeout=10
 else
   set timeout=${2}
 fi

```

---

