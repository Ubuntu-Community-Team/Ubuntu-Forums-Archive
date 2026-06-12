---
title: "Updating from 12.04 to 12.10 - unity bar doesn't work"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by St4rKiller070 on 2012-10-28
Hi,
Yesterday I update my Ubuntu 12.04 system to 12.10.
Unfortunately, unity bar does'nt work :/ When I log in I see only my wallpaper and that's all ^^
I can't do anything (except log out (ctr+alt+del)).
I suspect graphics card is not supported in the newest Ubuntu.
What should I do? How to fix it? Or how to do downgrade back tu Ubutnu 12.04?
Thank you in advance.
[SIZE="1"]And sorry for my english ;) I know, really bad.[/SIZE]

---

### Post by bogan on 2012-10-28
Hi!,** st4rKiller070**,

It is not clear from your Post whether you get a Log-in screen & can log-in.
If you can, Right Click on the Desktop Screen and select : 'Select Desktop Background': Can you change the Background?

What video card do you have ? Is there integrated Graphics ?

Does  it boot and run correctly from a LiveCD/USB?

If you can get to a Terminal - Press 'Crtl+Alt+t', or 'Crtl+Alt+F1' and login, run the following and Post  the results here: ```
name -r
lsp[ci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
``` Together with details of your computer set-up and type of installation -Wubi, direct install, dual with Windows, Ubuntu version??

[Copy/Paste command & output to a 'New Reply' edit box, highlight it and Click the '#' symbol in the Toolbar at the top of the edit box, to make it easy to read.]

Chao!, **bogan**.

---

### Post by St4rKiller070 on 2012-10-28
> **bogan said:**
> Hi!,** st4rKiller070**,

It is not clear from your Post whether you get a Log-in screen & can log-in.
If you can, Right Click on the Desktop Screen and select : 'Select Desktop Background': Can you change the Background?

What video card do you have ? Is there integrated Graphics ?

Does  it boot and run correctly from a LiveCD/USB?

If you can get to a Terminal - Press 'Crtl+Alt+t', or 'Crtl+Alt+F1' and login, run the following and Post  the results here: ```
name -r
lsp[ci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
``` Together with details of your computer set-up and type of installation -Wubi, direct install, dual with Windows, Ubuntu version??

[Copy/Paste command & output to a 'New Reply' edit box, highlight it and Click the '#' symbol in the Toolbar at the top of the edit box, to make it easy to read.]

Chao!, **bogan**.

1. Yes, i can change background
2. My video card: Asus eah6850
3.I don't know. I haven't got any CD with Ubuntu 12.10 now.
4.Terminal don't know what is "name" (first line). Code doesn't work.
5.Sorry, I don't understand question. :mad: I have Windows and Linux on my computer.

---

### Post by bogan on 2012-10-28
Hi!, **St4rKiller070,**

Sorry, my typo: commands should be: ```
uname -r
lspci -nnk | grep -iA3 vga 
/usr/lib/nux/unity_support_test -p
```Enter each command line separetly and press 'Enter'.

The Request:> details of your computer set-up and type of installation -Wubi, direct install, dual with Windows, Ubuntu version?? meant:

A. What Make & model is your computer? Desktop 0r Laptop? Which  CPU, GPU? How much memory?

B. Was 12.04 installed directly? or as a Windows program with 'Wubi'? ie. 'directly' ' dual with Windows' means installed in separate partitions.

C. Ubuntu version? would be answered by 'uname -r', provided you are not using Lubuntu, Kubuntu, Mint, Xcde or whatever else.

D. Which Video card/GPU?  would be answered by the 'lspci' command & it will also tell what driver is being used.

The last command will tell if Unity is supported.

Actually the Asus eah6850 card has an AMD Radion HD6850 GPU.

I take it you can get to a Terminal, so please also run:```
 sudo apt-get install linux-headers-generic
``` and note if it says it has installed it or it 'is already the latest version'.

As many people have had the same problem due to this file being missing.

Chao!, **bogan.**

---

### Post by IvorEd on 2012-10-28
This happened to me also and I was unsure of how to proceed.  I was able to operate under the Gnome desktop but Unity had vanished!

I've just uninstalled and reinstalled the newest version via WUBI.  Bit of a pain but it has fixed the problem.  Now just need to work out what's happened to my wireless connection...:P

---

### Post by cangelim on 2012-11-15
Hi. I had the same problem, also with a dialog saying compiz had errors.

In my case, I used synaptic package manager

$> sudo synaptic

Then, marked for 'complete reinstall' the following packages:

- libglib2.0.0
- compiz
- compiz-core
- compiz-plugins-default

Leaving synaptic, I rebooted:

$> sudo shutdown -r now

Worked for me. 

Good luck!

---

