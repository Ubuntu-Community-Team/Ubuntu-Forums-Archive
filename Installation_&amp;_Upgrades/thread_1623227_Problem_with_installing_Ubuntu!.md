---
title: "Problem with installing Ubuntu!"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Gummi on 2010-11-16
Ubuntu 10.10 is currently installing on my computer, I think. 
You see I didn't get the welcome screen I thought I'd get. Instead it goes straight to a command line screen where I can do absolutely nothing. I really can't be bothered with writing everything that's on the screen but here is the last line.
```
[     0.518322]  [<ffffffff8100aee0] ? kernel_thread_helper+0x0/0x10
```

I at first just left it there thinking it would just install, but when I came back nothing had changed, at all.
So I shut the computer down and turn it on again, but then comes the screen where I'm asked whether I'd like to boot from windows or ubuntu, I choose the latter. Then I'm sent to the same screen as before but now the first number is different.

Now, I'm not very good with computer especially this sort of thing, and it's actually quite typical that I land in these sort of things. So I really need help.

P.S. if this thread already exists I apologise, I didn't find it.

---

### Post by Gummi on 2010-11-16
Ok, a little development. I restarted the comp. once more and got into the welcome screen and went to install ubuntu. But the same command line screen appeared but with different numbers again.

Edit: same thing happens no matter what I choose from the welcome screen

---

### Post by oldfred on 2010-11-16
What video card do you have. Is this a very new system or older system? 

Try pressing any key right at the start (you should see stick figure & keyboard icons at bottom of screen) and see if you get the choice to choose f6. From f6 try the nomodeset option. There are many options to get systems to work that do not start normally.

The lines you are seeing are the standard boot lines. Normally they are hidden and are written into log files, but sometimes we want to see them as the last one may say more about what the problem is. The first entry is the time from start of boot, and sometimes very long times between entries is where a problem is also.

Aslo Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

