---
title: "Help! Trapped in Redhat!"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by rodeosmurf on 2005-05-14
It seems I have quite a mess on my hands. I was having a few problems with ubuntu, so I stupidly decided to get out my old Redhat 8.0 cds and give that a shot. Now I'm trapped in this wonky OS with no clue how to do anything. The main reason I needed to get my computer working was so I could burn a CD, but I can't even figure out how to do that in Redhat. Now I just want to burn myself a new copy of ubuntu, since I left my original one at my parents' house. Could any of you clue me in as to how to burn a cd in Redhat? I don't even know how to install new programs because I got so spoiled with apt-get and ubuntuguide.org.  ](*,)

---

### Post by Mike Buksas on 2005-05-14
[QUOTE=rodeosmurf]It seems I have quite a mess on my hands. I was having a few problems with ubuntu, so I stupidly decided to get out my old Redhat 8.0 cds and give that a shot. Now I'm trapped in this wonky OS with no clue how to do anything. The main reason I needed to get my computer working was so I could burn a CD, but I can't even figure out how to do that in Redhat. Now I just want to burn myself a new copy of ubuntu, since I left my original one at my parents' house. Could any of you clue me in as to how to burn a cd in Redhat? I don't even know how to install new programs because I got so spoiled with apt-get and ubuntuguide.org.  ](*,)[/QUOTE]
 The quickest way is from the command line. Check to see if you have cdrecord. (Just try it at a command line). If so, do: cdrecord -scanbus. This should come back with a table, mostly empty, but with an entry for your CD burner consisting of three numbers, like 1,0,0.

If you're making an Ubuntu CD then you've probably downloaded an iso file. This can be burned directly to the disk (other types of files need to be combined into an iso file first with mkisofs). Depending on the device numbers for your burner the resulting command will be:

cdrecord dev=<device numbers> <filename.iso>

Where the device numbers is something like 1,0,0, depending on the output from -scanbus.

Let me know if this is not helpful enough. The man page and cdrecord --help also have more information.

Good luck.

---

### Post by rodeosmurf on 2005-05-14
[QUOTE=Mike Buksas]The quickest way is from the command line. Check to see if you have cdrecord. (Just try it at a command line). If so, do: cdrecord -scanbus. This should come back with a table, mostly empty, but with an entry for your CD burner consisting of three numbers, like 1,0,0.

If you're making an Ubuntu CD then you've probably downloaded an iso file. This can be burned directly to the disk (other types of files need to be combined into an iso file first with mkisofs). Depending on the device numbers for your burner the resulting command will be:

cdrecord dev=<device numbers> <filename.iso>

Where the device numbers is something like 1,0,0, depending on the output from -scanbus.

Let me know if this is not helpful enough. The man page and cdrecord --help also have more information.

Good luck.[/QUOTE]
Thanks so much! I'm posting this from ubuntu right now!  :grin:

---

### Post by Mike Buksas on 2005-05-15
[QUOTE=rodeosmurf]Thanks so much! I'm posting this from ubuntu right now!  :grin:[/QUOTE]

Great! Glad I could help.

---

