---
title: "intel DP965 install nightmare"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by junglistmaster on 2006-10-22
i have spent a whole day trying to install dapper and edgy in all the different forms i have downloaded and failed.
all the forums say there is a problem with sata drives but i have worked out its a problem with intels new motherboards.
intels website list some linux distros that will work without other drivers; red flag and mandrake 2007.
i dont want either of these and would love ubuntu.
i just cant get past the install not recognising cd rom drive! i have used edgy rc and that doesnt work still.

---

### Post by kondor on 2006-10-22
1. Is BIOS set to boot from CD-Rom first?

2. Have you checked the MD5 hash to verify that the CDs are good?

3. Are you downloading the alternative 6.06.1 or the LiveCD version? The alternate is best for install. 

It has been awhile since any Linux distro had a problem with SATA. 

You say the install won't recognize the CD-rom, so how do you know there is a SATA drive recognition problem? Are you burning your downloaded CDs with WinXX or Linux? If WinXX, you have to copy the ISO image to the CD when you burn it.

---

### Post by wilsonywx on 2006-10-22
Well I have a DP965LT motherboard and I can't install using any Ubuntu cds. Search "jmicron" will bring up problems ubuntu has with the jmicron sata controller and the ich8 ide controller on the board. ALthough some people recently claimed successful install of ubuntu on i965 based boards, it still won't work for me. So I am using mandriva until ubuntu incorporates a fix for the ide thing (doesn't it suck that commercial software always have faster support for new hardware than community based ones?)

---

### Post by junglistmaster on 2006-10-23
i agree about the comercial software comment. still i love ubuntu and have read that the next kernal release(Kernel 2.6.18 ) will support the 965 series and pata/sata drive issues, so....
hopefully we'll be on edgy soon!

---

