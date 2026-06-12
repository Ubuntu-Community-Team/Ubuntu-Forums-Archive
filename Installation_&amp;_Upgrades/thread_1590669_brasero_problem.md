---
title: "brasero problem"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-10-08
I installed Ubuntu 10.04 three months back. The Brasero was working fine. But now when I want to 'Disk Copy' it is showing error '/usr/bin/toc2cue' is needed. Any help will be highly appreciated.

---

### Post by P4man on 2010-10-08
Make sure you enabled multiverse repository in software sources, then install cdrdao in synaptic (or apt-get install cdrdao)

---

### Post by gpdas on 2010-10-09
Can you pl tell how to add 'Multiverse Repository' !!! 
Thanks in advance.

---

### Post by P4man on 2010-10-09
Open the ubuntu software center, edit, software sources, on the first tab, enable "software restricted by copyright or legal issues (multiverse)".

---

### Post by gpdas on 2010-10-09
I checked that. It was already enabled. So I gave the command 'sudo apt-get install  cdrdao'  It is installed. Now when I start using 'Copy Disc' it shows  the error 'Install cdrdao manually'. That I have already done. The error  log file is created. I copied it and pasting here.

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)

---

### Post by P4man on 2010-10-09
Hmm odd. FWIW, it works here, and if I go in to Brasero > Edit > plugins > cdrdao it is greyed out, but checked. Kinda hard to see, but its enabled and I can configure it. Can you?

Anyway try purging and reinstalling brasero:
```

sudo apt-get purge brasero
sudo apt-get install brasero
```

---

### Post by gpdas on 2010-10-11
No, It did not work.

---

### Post by GingerAlex on 2010-10-12
I have had a similar problem (using Lucid Lynx), it said install crddao manually when I tried to copy an audio CD.

I can confirm cdrdao is installed properly and working, because I went to the command line and ran it.. after a bit of reading the instructions I just put my CD in and ran

```
cdrdao copy
```

and it copied the (audio) CD with a little prompt 1/2 way through to enter a blank disc and generally did a smashing job.

But it would be nice for those of us who are W.I.M.P.S at heart if Brasero did what it said on the tin..

---

### Post by gpdas on 2010-10-27
[SOLVED]  Actually it was taking a format .toc automatically. I have not noticed that. When I clicked 'Properties' and selected ISO, then everything was OK. Now I am happy with Brasero.

---

