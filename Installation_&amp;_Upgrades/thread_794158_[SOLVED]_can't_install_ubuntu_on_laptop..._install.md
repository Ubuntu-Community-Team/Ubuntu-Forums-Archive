---
title: "[SOLVED] can't install ubuntu on laptop... installer breaks after Configure the netwo"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by lelizondob on 2008-05-14
Hi, I've been using Ubuntu for 5 months as my primary os. I wanted to install ubuntu on and old laptop so I've boot with the alternate cd.. everything seems to go fine but when i reach the "Configure the network" step and I say "Do not configure network" the installer goes back to the Installer main menu and then I can't  select any step, the next step would be to detect disks, I've tried to skip this step, go back one step (to the detect network hardware) and nothing.

I've also downloaded the hardy live cd and it just freezes at 22%.

Then I tried to install gutsy, first with the alternate installer, it goes the same way than hardy, the installer goes back to the main menu and I can't go on. With the Live CD it freezes but I don't remember at what %.

It's and old laptop Toshiba Satellite with one problem, sometimes the Windows Key get stuck (that's the main reason I want to get rid of windows) but that souldn't be a problem in text mode right? There's also another weird problem. When I boot with the live cd (hardy and gutsy) the keyboard doesn't work, at least not the letters, just the enter, the backspace, control, alt, delete and the Fs, but if I type any letter at all it wont type anything. But if I go and open a terminal everything works! so I have to copy & paste the username, password, computer name etc from the terminal to the installer.

Thanks in advance

Luis

---

### Post by tribaal on 2008-05-14
Hum lets go through the basics first:

- Did you try a memtest ? (from the cd's boot menu, you need to leave it run through at least one pass)
- Also in the cd's boot menu, did you "Check CD for defects"? 

This really looks like a bad burn to me, hopefully this will be it.
Otherwise, did you try setting up the network by dhcp, failing, and just selecting "configure later"?

Cheers

- Trib'

---

### Post by lelizondob on 2008-05-14
thanks for the reply tribaal

I ran a memtest, there's no errors and 2 passed..

the cd has no burning errors and I did select "configure later" after the installer fails to configure dhcp network.. I can't even configure dhcp after it fails, if I select configure later or configure dhcp manually it just takes me to the installer menu..

should I try some special options when running the installer? and if I do which ones?

I never had any major problems installing ubuntu before and I have 2 pc running it without any problems.

The live cd runs without problems, everything works (except for the keyboard, it only works with the terminal).. the problem is just when I try to install

---

### Post by wpshooter on 2008-05-14
How much memory does this computer have ?

---

### Post by lelizondob on 2008-05-14
256mb

---

### Post by lelizondob on 2008-05-15
I've tried installing several ubuntu based distributions.. mint, gos, xubuntu, kubuntu and none of them worked, keyboard is a big problem and the installer just freezes, gos is the only one who tells me that my cd is not burned correctly, it's ironic because when i check the cd it tells me it's ok. xubunto, kubunto and mint are burned ok but I just can't install...

I tried dslinux and everything worked, although is a very fast dist it's very limited.. I finally could install Mandriva without any errors at all, the keyboard is working fine and everything was detected out of the box.

I love ubuntu, but I like algo having a working laptop, for my laptop ubunto was not an option.

---

