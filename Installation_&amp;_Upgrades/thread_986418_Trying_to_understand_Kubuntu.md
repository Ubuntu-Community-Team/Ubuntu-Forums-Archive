---
title: "Trying to understand Kubuntu"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by davzplace38 on 2008-11-18
I successfully downloaded Kubuntu "into" windows vista as a program, but my Nvidia drivers gave the screen fits. There was a "proprietory driver issue" with nvidia, but it recommended drivers 177.
There were "a lot" of upgrades that just said "failed". Did this have anything to do with a server being down, or was this a general failure withing Kubuntu system? Or was it because it wasn't a "stand alone operating system". I have a HP Media center with a 320gb drive. The model number is M8200N, and it has built in nvidia, but I installed a 8400 GS graphics out card. Can anyone explain some of this stuff and where I can actually read "computer language" that I can understand?

---

### Post by Partyboi2 on 2008-11-18
Are you able to post the message you got when your upgrades failed?

---

### Post by davzplace38 on 2008-11-18
Unfortunately I wasn't able to write them "all down". But there were numerous ones that failed, and it made me think it was a server issue regardless. I got the Kubuntu off of a download site and burnt the ISO image. Should I have just gotten a copy from Kubuntu sent to me? I really would like to learn linux, because It seems to offer more programs than windows.

---

### Post by Partyboi2 on 2008-11-18
Open a terminal (K Menu>System>Konsole) and type
```
sudo apt-get update
```
```
sudo apt-get upgrade 
``` and post the outputs.

---

