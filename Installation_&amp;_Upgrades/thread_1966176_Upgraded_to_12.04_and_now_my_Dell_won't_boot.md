---
title: "Upgraded to 12.04 and now my Dell won't boot"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by gurokko on 2012-04-26
I apologize for any grammatical mistakes, I have to post this from my phone.  I upgraded from Oneric Ocelot to Precise Pangolin last night, and now my computer completely refuses to boot.  It acts fine until it reaches a certain point, and then hangs indefinitely.  I have left it sitting for hours and it does nothing.  I have some screencaps is where it hangs... can anyone pleased help me?  My laptop is useless now :(

---

### Post by LinuxFan999 on 2012-04-26
You will need to reinstall Ubuntu 12.04. Download an ISO image of Ubuntu 12.04, boot from it, and do a clean installation.

---

### Post by gurokko on 2012-04-26
Won't that get rid of everything I had on the hard drive?  :(  Gosh... well, thank you for the guidance.

---

### Post by jadtech on 2012-04-26
i beleive if you  boot from live cd you may be able to mount you home or root  partition  and at the least salvage  some files and such  ..


I wouldnt dump  everything just yet  some one out there may have a solution for this to at least get you booted back in ..

everyone here has been pressing this for as long as I been on this forum BEfore you upgrade back up your system ..

---

### Post by LinuxFan999 on 2012-04-26
> **gurokko said:**
> Won't that get rid of everything I had on the hard drive?  :(  Gosh... well, thank you for the guidance.
You can back up your data from your home folder while running the live CD.

---

### Post by gurokko on 2012-04-26
Oh, thank you!  Yes, I have definitely learned my lesson about backing up before you upgrade.  From here on out I'll be more careful.  Thanks again.

---

### Post by Scooby-2 on 2012-04-27
Hi

Be warned that your Dell may not boot from the 12.04 CD. I have a HP Compaq nx6325 which will not boot from the Xubuntu 12.04 CD.  My display shows what is in the attachment. There is no mouse, no menu, and the hard disk light is permanently on and the CD stops spinning after a couple of minutes.

gurokko - I suggest you boot from a Knoppix CD to back up your data first - then try again.

Edit: I downloaded ubuntu-12.04-desktop-i386.iso (i.e. NOT Xubuntu) and this boots OK. However while I was trying to find the menus (these have disappeared!) the laptop started continually reading/seeking the CD-ROM and became unusable. I had to power the system off in the end.

For anyone looking, the MD5 sums I get (Can't find them on-line, so cannot say if hey are correct):
52fddd81e75bb421a5435a42ca9ec6df  xubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso

---

### Post by gurokko on 2012-04-28
Hi everyone!  Just replying to let you all know that I was able to use a Fedora live boot CD I had laying around to mount my hard drive and get all my important things, pictures and stuff, moved to an external hard drive.  I did a clean install of 12.04 from the disc and it worked like a charm!  Everything's back to working the way it should.

Thank you so much for your help!

---

### Post by jadtech on 2012-04-28
glsd everything worked out for you :)

---

### Post by Scooby-2 on 2012-04-29
> **Scooby-2 said:**
> Hi

Be warned that your Dell may not boot from the 12.04 CD. I have a HP Compaq nx6325 which will not boot from the Xubuntu 12.04 CD.  My display shows what is in the attachment. There is no mouse, no menu, and the hard disk light is permanently on and the CD stops spinning after a couple of minutes.

gurokko - I suggest you boot from a Knoppix CD to back up your data first - then try again.

Edit: I downloaded ubuntu-12.04-desktop-i386.iso (i.e. NOT Xubuntu) and this boots OK. However while I was trying to find the menus (these have disappeared!) the laptop started continually reading/seeking the CD-ROM and became unusable. I had to power the system off in the end.

For anyone looking, the MD5 sums I get (Can't find them on-line, so cannot say if hey are correct):
52fddd81e75bb421a5435a42ca9ec6df  xubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso

Got to the bottom of the problem - a faulty CD-RW. I used a bash script to read the CD and generate the MD5 sum and compare it with those listed above. Pity Xfburn doesn't have a "Verify written data" option.

Incidentally, those MD5 sums above are correct, confirmed here:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Torgas Prim on 2012-04-30
So far, knock on wood, I did the upgrade from 11.10 last night. Only had ATI drivers and Wine installed previously. This was a new install. Have not had chance to poke around yet, but looks like this upgrade went well. Yay cause I wont ever go back to windows personally. 
Once I tested GW2 works on Ubuntu....I flew to the upgradeas fast as I could :KS

---

