---
title: "Not getting a list of bootable OSes."
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Ghostlove on 2011-05-24
So I wanted to dual boot Windows 7 and Ubuntu 11.04. I partitioned my drive a long time ago, leaving 50g or so free for the Windows install, and installed Ubuntu on the remaining 250g partition. I know, I know, you're supposed to install Windows first. Today I installed Windows on the remaining 50g partition.

Now when I switch my computer on, Windows 7 automatically loads up. I don't want it to do this. I want it to give me the list of possible operating systems and be able to choose whether to use Ubuntu or Windows. At the moment I can't get into my Ubuntu partition at all because Windows has just... taken over.

Could someone help me to get that list of possible OSes back? Bear in mind that though I've been using Ubuntu since 2007 I'm still pretty much a newbie when it comes to this sort of thing and will probably need my hand holding. There will be virtual tea, biscuits and cuddles in it for you.

---

### Post by sisco311 on 2011-05-24
You have to reinstall Grub2. Follow this guide: [uhelp]community/Grub2#Reinstalling GRUB 2[/uhelp]

If you need more help, please feel free to ask.

---

### Post by Ghostlove on 2011-05-25
I followed those instructions to the letter and when I got to sudo update-grub I got the following error:

```
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

Any ideas, please? :/

---

### Post by Rubi1200 on 2011-05-25
> **Ghostlove said:**
> I followed those instructions to the letter and when I got to sudo update-grub I got the following error:

```
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

Any ideas, please? :/

That error means you tried running the command from the live medium.

You need to run it once you are booted back into Ubuntu.

Let us know how things work out please.

---

### Post by Ghostlove on 2011-05-25
That's brilliant thank you, I appear to be able to choose which OS to log into now. You've been so helpful, thanks so much. :D

---

### Post by Rubi1200 on 2011-05-25
> **Ghostlove said:**
> That's brilliant thank you, I appear to be able to choose which OS to log into now. You've been so helpful, thanks so much. :D

No problem, you are more than welcome :-)

I am sure sisco311 will also be pleased.

If you can mark this thread Solved using the Thread Tools near the top of the page, it will help other users find a working solution if they ever find themselves in a similar situation.

Enjoy!

---

### Post by sisco311 on 2011-05-25
> **Ghostlove said:**
> That's brilliant thank you, I appear to be able to choose which OS to log into now. You've been so helpful, thanks so much. :D

Cool! I'm glad it worked.

---

