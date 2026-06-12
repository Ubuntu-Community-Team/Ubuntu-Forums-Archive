---
title: "Ugly boot experience"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nzjrs on 2009-09-28
Hi All,

Just checking if I am seeing what others see on boot, and if this is really considered an improvement on the boot experience in Jaunty (note: boot time is the same, ~15-20 seconds)

[LIST]
[*]After grub It drops to a text console where it sits for 3-4 seconds
[*]Xsplash starts,  animates for a few seconds
[*]GDM starts, I log in
[*]Xsplash takes over
[*]Desktop 'fades' in, then a few seconds later comes to life
[*]A few seconds pass before my background replaces the default one
[/LIST] 

Personally I preferred usplash, but I was just checking that I was not experiencing a bug at my machine (Macbook 2,1)

---

### Post by juancarlospaco on 2009-09-28
*Wheres the caotic problem...?*

---

### Post by SushiR on 2009-09-28
Same here. And the splash is REALLY ugly. This dark brown... OMG!

---

### Post by shafin on 2009-09-28
Calm down, it's just a testing OS and not the finished product.

---

### Post by ranch hand on 2009-09-28
[http://ubuntuforums.org/showthread.php?t=1277030](http://ubuntuforums.org/showthread.php?t=1277030)

---

### Post by novafluxx on 2009-09-28
> **nzjrs said:**
> Hi All,

Just checking if I am seeing what others see on boot, and if this is really considered an improvement on the boot experience in Jaunty (note: boot time is the same, ~15-20 seconds)

[LIST]
[*]After grub It drops to a text console where it sits for 3-4 seconds
[*]Xsplash starts,  animates for a few seconds
[*]GDM starts, I log in
[*]Xsplash takes over
[*]Desktop 'fades' in, then a few seconds later comes to life
[*]A few seconds pass before my background replaces the default one
[/LIST] 

Personally I preferred usplash, but I was just checking that I was not experiencing a bug at my machine (Macbook 2,1)

Same exact thing happens to me, the GDM background is totally different from XSplash, and from my desktop background, I am dropped to console after GRUB.

I'm also dropped to console on shutdown too, I never see usplash.

---

### Post by kansasnoob on 2009-09-28
It'll change somewhat yet before final.

Personally I liked the way Jaunty looked on boot. Seemed like a seamless boot to my new custom desktop:

[ATTACH]130100[/ATTACH]

Of course I owe that to Karmic development. That is I downloaded some Karmic packages to Jaunty to accomplish that.

---

### Post by Ric_NYC on 2009-09-28
I don't understand what's going on after something was broken 2 weeks ago.

Now when I boot the computer I have verbose mode, then xplash, then the login screen, then xplash again.

What is it?

I prefer the old way to boot the system. One "graphical" boot...
Besides that the booting process seems to be slower than it was in the other alphas.

---

### Post by nzjrs on 2009-09-28
> **shafin said:**
> Calm down, it's just a testing OS and not the finished product.

Quite lucky I was calm then!

---

### Post by joey-elijah on 2009-09-28
> **nzjrs said:**
> Hi All,

Just checking if I am seeing what others see on boot, and if this is really considered an improvement on the boot experience in Jaunty (note: boot time is the same, ~15-20 seconds)

[LIST]
[*]After grub It drops to a text console where it sits for 3-4 seconds
[*]Xsplash starts,  animates for a few seconds
[*]GDM starts, I log in
[*]Xsplash takes over
[*]Desktop 'fades' in, then a few seconds later comes to life
[*]A few seconds pass before my background replaces the default one
[/LIST] 

Personally I preferred usplash, but I was just checking that I was not experiencing a bug at my machine (Macbook 2,1)

It's the same for most people. Certainly is for me. Think of the entire boot process as an exclusively geeky USplash for the alpha. Seriously - come the RC you'll be trying to recreate it just to escape from the browwwwwwn.

---

### Post by ranch hand on 2009-09-28
The whole exercise is to get away from usplash in favor of xsplash which is supposed to be faster.

I believe that it will be once the verbose text is gotten rid of.

Don't get your panties in a bunch just yet, I think it will work out.

---

### Post by moviemaniac on 2009-09-28
> **nzjrs said:**
> Hi All,

Just checking if I am seeing what others see on boot


Here's what I get:

[LIST]
[*]Grub
[*]Usplash (white Ubuntu logo on black background)
[*]blinking cursor for half a minute
[*]tty1 (->manually switching to tty7)
[*]Xsplash starts,  animates for a few seconds
[*]GDM starts, I log in
[*]Xsplash takes over
[*]Desktop 'fades' in, then a few seconds later comes to life
[*]A few seconds pass before my background replaces the default one
[/LIST]

---

### Post by nzjrs on 2009-09-28
> **ranch hand said:**
> The whole exercise is to get away from usplash in favor of xsplash which is supposed to be faster.

I believe that it will be once the verbose text is gotten rid of.

Don't get your panties in a bunch just yet, I think it will work out.

My panties are not bunched.

---

### Post by nzjrs on 2009-09-28
> **moviemaniac said:**
> Here's what I get:

[LIST]
[*]Grub
[*]Usplash (white Ubuntu logo on black background)
[*]blinking cursor for half a minute
[*]tty1 (->manually switching to tty7)
[*]Xsplash starts,  animates for a few seconds
[*]GDM starts, I log in
[*]Xsplash takes over
[*]Desktop 'fades' in, then a few seconds later comes to life
[*]A few seconds pass before my background replaces the default one
[/LIST]

Hmm interesting. I do not get a Usplash screen, just dmesg spew, and I can't see a tty switch.

---

### Post by moviemaniac on 2009-09-28
> **nzjrs said:**
> Hmm interesting. I do not get a Usplash screen, just dmesg spew, and I can't see a tty switch.

When I use the -10 kernel, that's what I get too. With the -11 kernel however I get the boot "experience" as described above.

---

### Post by merlyn on 2009-09-29
Kubuntu (Karmic) latest image + current updates = no splash of any kind on boot.

I do however get the old Jaunty style usplash on shut down.

Is this yet another example of poor kubuntu polish compared to ubuntu?

---

### Post by tjeremiah on 2009-09-29
I like the brown :)

---

### Post by excogitation on 2009-09-29
Seems my daily updated installed version isn't up to par with the daily live CD ... what a shame.

Installed:
    * Grub
    * Bar 6 warning
    * blinking cursor ~30s
    * boot messages
    * Xsplash starts, animates for a few seconds
    * GDM starts, autologin (drums)
    * Xsplash takes over
    * Desktop 'fades' in, then a few seconds later comes to life
    * A few seconds pass before my background replaces the default one

With the daily-live usplash (white Ubuntu logo on black background)
does work.

---

### Post by cyberkilla on 2009-09-29
Yeh, I get a 40-60 second delay before xsplash actually appears too;)

---

