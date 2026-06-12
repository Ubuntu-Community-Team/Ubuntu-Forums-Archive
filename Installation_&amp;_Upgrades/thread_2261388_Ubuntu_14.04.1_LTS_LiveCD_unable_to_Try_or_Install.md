---
title: "Ubuntu 14.04.1 LTS LiveCD unable to Try or Install Ubuntu"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by FourDii on 2015-01-18
Hello
I'm completely new to Ubuntu related stuff, so go a bit easy on me. 

I'm planning on migrating from Windows 8.1 (pre-installed on an ASUS Desktop) to Ubuntu, however I can't seem to try or install Ubuntu as it gives me this: "kernel panic not syncing fatal exception in interrupt" then something along the lines of Switching back to a text console. It freezes after that, and I'm forced to restart.

Any help?

---

### Post by sudodus on 2015-01-19
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and ***model*** (the ASUS models can be quite different)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier to give relevant help. But I will start with this general tips:

- Please check with ***md5sum*** that the download was good. See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Try to burn a new DVD, this time with the lowest possible speed.

-o-

Kernel panic is not nice. Things might work better, if you try some of the boot options. You can start with nomodeset which is aiming at the graphics. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If still no success, I suggest that you try another version of Ubuntu. The one you are trying, ***14.04.1 LTS*** is the one I would recommend as the first choice, but an older version might be better with older hardware: ***12.04.5 LTS***, and a newer version might be better with new hardware: ***14.10*** or even the version being developed right now, ***Vivid Vervet***, to become 15.04 in April. (You can find the ***current daily build*** via the [iso qa-tracker]("http://iso.qa.ubuntu.com/").)

---

### Post by Elfy on 2015-01-19
> **sudodus said:**
> ... or even the version being developed right now, ***Vivid Vervet***, to become 15.04 in April. (You can find the current daily build via the [iso qa-tracker]("http://iso.qa.ubuntu.com/") and select either the alpha build or the current daily build.)

IF you DO try the dev version then don't bother with the alpha - just go straight to the daily - save yourself the updates you'll immediately get. In addition the alpha (iirc) still had the old 14.10 kernel.

Any support for that version should be in [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by grahammechanical on 2015-01-19
It could also indicate something going wrong with the hardware. If you can run the installation disc again and at the first purple screen press enter. At the second screen select the language (English is default) and at the underlying screen select either Check disc for defects or Test memory or run both.

Regards.

---

### Post by FourDii on 2015-02-10
Hello again.
Sorry, I was out on vacation and I left my PC behind.
Anyway, I managed to get a screenshot of the error, it's not the best, but here you go.
[IMG]http://i.imgur.com/AFQFYm9.jpg[/IMG]
As for what sudodus asked me to specify

[COLOR=#000000]1 - Brand name and [/COLOR][I]**model** (the ASUS models can be quite different 
2 - CPU
3 - RAM (size)
4 - graphics chip/card
5 - wifi chip/card

[/I]1. ASUSTeK COMPUTER INC. M11BB or something like that
2. AMD A10-6700
3. DDR3 8192 MB
4. ATI AMD Radeon HD 8670D
5. Realtek 8821AE Wireless LAN 802.11ac PCI-E NIC

I rammed my way through 3 discs already with 3 different burning softwares and I get the same result.

Again, sorry for late.

---

### Post by FourDii on 2015-02-10
> **grahammechanical said:**
> It could also indicate something going wrong with the hardware. If you can run the installation disc again and at the first purple screen press enter. At the second screen select the language (English is default) and at the underlying screen select either Check disc for defects or Test memory or run both.

Regards.

Tried both, everything was reported normal.

---

### Post by sudodus on 2015-02-11
> **FourDii said:**
> Hello again.
Sorry, I was out on vacation and I left my PC behind.
Anyway, I managed to get a screenshot of the error, it's not the best, but here you go.
<snipped screenshot>
As for what sudodus asked me to specify

[COLOR=#000000]1 - Brand name and [/COLOR][I]**model** (the ASUS models can be quite different 
2 - CPU
3 - RAM (size)
4 - graphics chip/card
5 - wifi chip/card

[/I]1. ASUSTeK COMPUTER INC. M11BB or something like that
2. AMD A10-6700
3. DDR3 8192 MB
4. ATI AMD Radeon HD 8670D
5. Realtek 8821AE Wireless LAN 802.11ac PCI-E NIC

I rammed my way through 3 discs already with 3 different burning softwares and I get the same result.

Again, sorry for late.

Please describe the situation leading to the screenshot:

- Did you 'try Ubuntu' (booting from a DVD/USB drive)?
or
- Did your boot from an installed system?

The graphics card (AMD) indicates that you may have better results with a proprietary driver, but there might be other issues too. It might be worthwhile to try some boot options according to the following link (try several boot options, one or several each time, you can start with nomodeset)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by FourDii on 2015-02-11
> **sudodus said:**
> Please describe the situation leading to the screenshot:

- Did you 'try Ubuntu' (booting from a DVD/USB drive)?
or
- Did your boot from an installed system?

The graphics card (AMD) indicates that you may have better results with a proprietary driver, but there might be other issues too. It might be worthwhile to try some boot options according to the following link (try several boot options, one or several each time, you can start with nomodeset)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I did try booting from a DVD.

I'll try other boot options later today.

---

