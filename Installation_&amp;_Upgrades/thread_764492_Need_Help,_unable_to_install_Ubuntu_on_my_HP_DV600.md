---
title: "Need Help, unable to install Ubuntu on my HP DV6000z"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Cali_bear2003 on 2008-04-23
Hello,
I have an HP DV6000z. I have been unable to load any of the version up until this point. When the beta version of 8.04 came out, I thought I would give that version a try. All of the previous versions would start to load and then just hang at a black screen. The 8.04 has been different so far. It allows me to go through all the needed steps and then installs up to 87%. At this point the system just hangs. I have tried numerous times and even burned my disk at 12x thinking maybe my reader was having issue's reading at a higher rate. I am really stumped and know longer know where to turn. Here are the spec's of my laptop:
-HP Dv6000z
-AMDx64 TK-53 Athlon 1.7 processor
-4gb ram
-Vista 64 bit
-6150 Nvidia video card
- The rest is the basic HP installed standard hardware/software. I had the 32 bit vista installed prior, but with the same issue's. I only went to the 64 bit to see the difference in performance. I know that my knowledge is far below everyone else here, so I will thank everyone now in advance for ANY insite as to HOW I can load this OS. Also, I know knowthing about editing anything from the command prompt, so if there is a solution from that end, I will need to be treated like a 5 year old with my hand held throught the process. Thanks so much guys for any help. I have a feeling it is the Athlon processor that is holding up everything. My co-workers have the same system with the same spec's. The only difference is that they are running the Turion processor. Hmmmmmmmm.......
Thanks again!!!

---

### Post by tyblu on 2008-04-24
Perhaps a common nVidia video driver problem:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by dstew on 2008-04-24
First, make sure the disk is good. Check the disk integrity (menu item on opening screen). If the disk is OK there are several things you can try. But make sure the disk is OK first. Does this same disk install the system on the other computers OK?

---

### Post by Pumalite on 2008-04-24
dv6000 have special problems. Something to read:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by Cali_bear2003 on 2008-04-24
Hello,
Yes, I did check the disk and it came back without errors. I was able to load this without problems on an older XP box. I also reburned the disk as a slower speed in the case that my reader was having issue's with a higer read speed. The end result has been the same. I am now downloading the final of 8.04 LTS, maybe I will have different luck with that version. Has there been any changes made from the beta version???

---

### Post by dstew on 2008-04-25
The disk is fine. The problem is that it is having some trouble dealing with your hardware. This is a fairly common problem with the Live CD. You can try to get the Live CD to boot using kernel parameters. Press F6 at the opening menu, and enter the parameters on the kernel line. Try these:```
noapic nolapic acpi=off
```You can try them alone, or in combination. See [this wiki]("https://wiki.ubuntu.com/HP_dv6000_Series") for more advice.

If you still can't get the Live CD to work, try the Alternate Install CD. It installs the same Ubuntu desktop system, but it uses a text-based installer that works more reliably. You get it from the Ubuntu download page, check the box below the Start Download button.

---

### Post by Pumalite on 2008-04-25
[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by Cali_bear2003 on 2008-04-25
Well, I finally was able to download the final yesterday with too me about 7+ hours. I burned the iso and it loaded successfully today. What a relief. I guess this latest version has the missing drivers that many of the other versions lacked. Thank you everyone for all of the input.......

---

### Post by chris.raighn on 2008-04-26
I had a similar problem I too have a dv6000z with NVidia graphics, it froze at %15. so the next time I moved the mouse every so often and it installed.

---

