---
title: "Mplayer installation - codecs - skins - source and binaries"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by teaguepatrick on 2007-01-04
OK

So I finally installed Mplayer - kinda - minus the codecs, skin, source and binaries. Now I'm stuck. I've downloaded the codecs to my desktop and I'm working on the rest. I tried to paste the codecs folder into the Mplayer folder, but no worky. What do I do now??

---

### Post by pay on 2007-01-04
> **teaguepatrick said:**
> OK

So I finally installed Mplayer - kinda - minus the codecs, skin, source and binaries. Now I'm stuck. I've downloaded the codecs to my desktop and I'm working on the rest. I tried to paste the codecs folder into the Mplayer folder, but no worky. What do I do now??You can put the codecs anywhere but when you compile mplayer you would need to add the path to the codecs to the ./configure script```
./configure --enable-gui --with-codecsdir=/usr/local/lib/codecs/ --font=/path/to/font 
```Then to install a skin download the skin that you want form the mplayer site and extract it to /usr/local/share/mplayer/skins/

---

### Post by sdowney717 on 2007-03-03
OK, please why cant we get better more detailed instructions, so many posters just assume so much.

STEP5: Installing a GUI skin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unpack the archive and put the contents in /usr/local/share/mplayer/skins/ or
~/.mplayer/skins/. MPlayer will use the skin in the subdirectory named default
of /usr/local/share/mplayer/skins/ or ~/.mplayer/skins/ unless told otherwise
via the '-skin' switch. You should therefore rename your skin subdirectory or
make a suitable symbolic link.

Load up file browser click Places-Computer Select view hidden files

now navigate to /root/.mplayer  or I suppose your user folder
create a new folder called skins under the .mplayer folder
copy the downloaded extracted skin folder to ~/.mplayer/skin folder
Run gmplayer, right click the player window, select skins, the skin name should show up in the list.

---

### Post by sagara on 2007-03-19
Hi I downloaded a couple of skins for mplayer but realized that both the ~/.mplayer/**skins** and /usr/local/share/**mplayer/skins/** folders did not exist.

I manually created these folders and uncompressed the skin files there.  After loading mplayer and looking for the skins, the new skins didn't show up.

Did I miss anything?

---

