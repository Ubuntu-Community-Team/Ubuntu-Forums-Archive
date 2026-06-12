---
title: "Black screen"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by COLiNx86 on 2007-07-24
ok so i downloaded the AMD64bit Ubuntu 7.04 alternative download and burned it and installed it. everything went fine i think (well except the network i couldn't figure that out but anyways). so it says to take out the cd and reboot. i do that and it shows some white writing then it shows the orange loading bar then it shows some more white text then goes blank. i tryed press alt+f1 and ctrl+alt+f1 to boot into the cli or whatever but nothing happened it just sat there. did something go wrong in the installation?

---

### Post by nichipet on 2007-07-24
What does the white text say? If that was GRUB, it may have auto booted into the first option and that option may be having problems. You may need to select a different option to fix the problem.

---

### Post by COLiNx86 on 2007-07-24
> **nichipet said:**
> What does the white text say? If that was GRUB, it may have auto booted into the first option and that option may be having problems. You may need to select a different option to fix the problem.
it's something about the kernel and then it says like press Esc to get to the menu or somkething then a couple more lines that go away to fast to read

---

### Post by nichipet on 2007-07-24
The only thing I can think of off-hand is give it more time. Let it run for 5-10 minutes and see if it advances. What type of computer is it? If it's an older model it may just be slow in starting up.

Since you burned the disc it may be problems with the disc during installation. You could try burning at a slower speed and then reinstall to see if that helps.

---

### Post by COLiNx86 on 2007-07-24
> **nichipet said:**
> The only thing I can think of off-hand is give it more time. Let it run for 5-10 minutes and see if it advances. What type of computer is it? If it's an older model it may just be slow in starting up.

Since you burned the disc it may be problems with the disc during installation. You could try burning at a slower speed and then reinstall to see if that helps.
i let it sit until my computer automatically shut off(about 30 min).
it's brand new just got it in march Compaq presario v6000.
and i burned it using like 8X i don't think it will go slower than that.
ok i just saw it agian and it was a grub it told me to press esc to get to the menu so i did and now it says some boot options

---

### Post by skipjaxn on 2007-07-24
I have a similar problem loading Xubuntu on an IBM T21. I press esc on the opening screens and it dumps me to what looks like a run option menu of Ubuntu, Ubuntu (recovery mode), and Ubuntu Memtest86+. Choosing recovery mode, the laptop boots normally to a console. Typing X at the prompt and I get that same blank screen. So it sounds like it's an X-server issue. Any guidelines here. I know the T21s use Savage video.

---

### Post by nichipet on 2007-07-24
Try getting to the GRUB screen again and then using the arrows to select a different option. Especially if you have a safe mode or recovery mode listed, try that one.

---

### Post by nichipet on 2007-07-24
> **skipjaxn said:**
> I have a similar problem loading Xubuntu on an IBM T21. I press esc on the opening screens and it dumps me to what looks like a run option menu of Ubuntu, Ubuntu (recovery mode), and Ubuntu Memtest86+. Choosing recovery mode, the laptop boots normally to a console. Typing X at the prompt and I get that same blank screen. So it sounds like it's an X-server issue. Any guidelines here. I know the T21s use Savage video.

I don't know anything about the IBM T21, but you're right that it sounds like an X-server issue. The solution, I'm guessing, may be in /etc/X11/xorg.conf in the Device section for the video card, the Monitor section, or the Screen section.

---

### Post by COLiNx86 on 2007-07-24
ok i ran the recovery mode option and it did everything and is now saying root@Colin:~#

---

### Post by nichipet on 2007-07-24
> **COLiNx86 said:**
> ok i ran the recovery mode option and it did everything and is now saying root@Colin:~#

That's what recovery mode should do. Now you know it's X-server and not Ubuntu as a whole. Try this from that prompt:

```
sudo dpkg-reconfigure xserver-xorg
```

That will reconfigure your monitor and maybe fix the problem.

---

### Post by skipjaxn on 2007-07-24
Yep I just ran that command, allowed it to auto-detect the video card, took all the defaults, and I'm in business.

---

### Post by COLiNx86 on 2007-07-24
ok i got to the screen where i'm supposed to type the amount of memory(kb) to be used by the video card. how much am i supposed to put? does it matter?

---

### Post by skipjaxn on 2007-07-24
I chose no entry. I believe if you read the information on the screen, no entry is recommended.

---

### Post by COLiNx86 on 2007-07-24
> **skipjaxn said:**
> I chose no entry. I believe if you read the information on the screen, no entry is recommended.
oh ok i didn't know if i needed to put like how much i want it to use or something

---

### Post by COLiNx86 on 2007-07-24
for a laptop what kind of mouse would i have?

---

### Post by nichipet on 2007-07-24
I think just accept the default. Or look for a "pad" option, such as ThinkPad.

---

