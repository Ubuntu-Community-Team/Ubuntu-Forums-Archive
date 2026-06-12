---
title: "Flash player 9, sudo ./flashplayer-installer"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Linux_oid on 2007-03-20
[Adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW")  site "Installation instruction" offers only local installation. I try to use **sudo** command for global installation (*Adobe Flash Player 9 will be installed system-wide* in according to installer). 

 I reached a point 
*Please enter the installation path of the Mozilla, SeaMonkey, or Firefox browser (i.e., /usr/lib/mozilla):  * and just pressed enter.   I've got 

[B]* dir= /home/<user name>/install_flash_player_9_linux/* 
*WARNING: Please enter a valid installation path.*[/B].

When I added path 

[I]Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): [/I]  (typed **/usr/local/firefox** and pressed enter)  I've got this

 *[B]dir= /home/<user name>/install_flash_player_9_linux//usr/local/firefox*
*WARNING: Please enter a valid installation path.[/B]*

I played with that for two days in a row and finished up with a local installation. Any idea?

---

### Post by aysiu on 2007-03-21
Forget all that and follow these instructions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Linux_oid on 2007-03-21
That site doesn't answer my question about **sudo ./flashplayer-installer**. 

Whatever. I've installed it anyway.

---

### Post by aysiu on 2007-03-21
I have no idea what was going on there, but I linked you to instructions to install Flash globally (not locally). I thought you were trying to get Flash installed globally.

---

### Post by Linux_oid on 2007-03-21
I was interested  in doing this ***Adobe*** way. 

Anyway, it does look like something is wrong with my box. It still works however.

---

### Post by Linux_oid on 2007-04-02
Yeah! It was a problem  with box itself. On a just installed ubuntu 6.10 (another box)  have no problem with changing suggested directory **/usr/local/mozilla** to usr/local/firefox/.

At the end of installation, *Flash installer* is asking about creating symbolic link in */usr* directory. Just press Enter key.

[There ]("http://www.ubuntuforums.org") is another thread about local installation by the way

---

