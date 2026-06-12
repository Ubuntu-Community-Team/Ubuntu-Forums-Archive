---
title: "Van't get the the computer to boot from the CD"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by noteviljoe on 2006-06-21
I have downloaded Ubuntu and burnt it onto a CD (useing Nero)
If the CD is inserted if the computer on (running windows 98 ) the
"bowser" thingy comes up and it all looks good.

However when I try to boot from the CD, re-starting the computer
it just won't boot from the CD.

I have tryed:

*going into BIOS, looking under the boot section and making the
CD-ROM number 1 in the Boot secence list.

*Following [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
I ahve tryed Getting "Smart boot manager" from Smart Boot Manager, 
putting it on to a floopy and re-starting.
Then I get a list of opptions none of which seems to be CD-ROM?!

Possible issules:My CD drive broke and I replaced it with a freeby from
my Uncle, but it seems to run CDs fine.

Hope you can help or direct me to a different way to tryout Ubuntu,

Joe

---

### Post by rowanparker on 2006-06-21
When you say: "It wont boot", do you mean it just continues to boot windows or there is an error booting?

Rowan.

---

### Post by noteviljoe on 2006-06-22
It continues to boot windows as normal. The light on the CD drive does flash a little bit but it seems that the CD is ignored.

---

### Post by noteviljoe on 2006-06-22
I have just tryed going on BIOS and disableing all the boot devices other then the CD-ROM. Still it dosn't boot from the CD, it doesn't boot at all!](*,)

---

### Post by rcarring on 2006-06-22
You need to make the cdrom drive master on ide2 not slave on ide1.

---

### Post by noteviljoe on 2006-06-22
I'm not sure what you mean/not sure how I would go about doing that.

please treat me as a right thicky.

---

### Post by noteviljoe on 2006-06-22
On the BIOS set up utility, under the "main" section
there is the following that looks a bit like what you 
are talking about:

>Primary Master [ST3160023A] (I think this is my main hard drive)

>Primary Slave [Maxtor 2B020H1] (I think this is my old hard drive)

>Secondary Master [SAMSUNG CD-R/RW DRIVES]

>Secondary Slave [Auto]

Am I on the right track? How should I change this set up to make "the cdrom drive master on ide2 not slave on ide1.":confused:

---

### Post by noteviljoe on 2006-06-23
:confused:

---

### Post by bluenova on 2006-06-23
[QUOTE=noteviljoe]On the BIOS set up utility, under the "main" section
there is the following that looks a bit like what you 
are talking about:

>Primary Master [ST3160023A] (I think this is my main hard drive)

>Primary Slave [Maxtor 2B020H1] (I think this is my old hard drive)

>Secondary Master [SAMSUNG CD-R/RW DRIVES]

>Secondary Slave [Auto]

Am I on the right track? How should I change this set up to make "the cdrom drive master on ide2 not slave on ide1.":confused:[/QUOTE]

It already is, and I don't knwo why it would need to be any way. Are you sure it's a good disk, have you tried burning a new one at the slowest speed? If the light comes on on the CD drive after the first bit of booting, then it's looking for a bootable disk ok.

---

### Post by noteviljoe on 2006-06-23
I'll try to burn the CD again.

Note: I did have to delete a couple of programmes from the "programmes" file (Gimp and thunderbird) before I burned the CD, as i wouldn't fit. I imagined that they wouldn't be vital for loading the os and that I could download them later.

---

