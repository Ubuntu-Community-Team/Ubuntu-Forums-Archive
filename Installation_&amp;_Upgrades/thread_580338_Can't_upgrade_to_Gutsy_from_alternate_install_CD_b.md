---
title: "Can't upgrade to Gutsy from alternate install CD because of spaces in CD name"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mschersten on 2007-10-18
So, I decided not to to upgrade through the Update Manager because of bandwidth, and download the torrent of the alternate install cd and follow directions [here.]("http://www.ubuntu.com/getubuntu/upgrading")  I downloaded the .iso, and burned it using "CD/DVD Creator," which named the cd "Ubuntu 7.10 i386."  The upgrade dialog did not display, so I followed the instructions using gksu.  The problem here is that my "cdromupgrade" file is in /media/Ubuntu 7.10 i386, which has spaces in the filename.  So, when I run

```
gksu "sh /media/Ubuntu\ 7.10\ i386/cdromupgrade"
```

I get

```
Could not find the upgrade application in the archive, exiting
tar: /media/Ubuntu: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: 7.10: Not found in archive
tar: i386/dists/stable/main/dist-upgrader/binary-all//gutsy.tar.gz: Not found in archive
tar: Error exit delayed from previous errors
```

Here are some selected lines from the cdromupgrade script:

```
CODENAME=gutsy
UPGRADER_DIR=dists/stable/main/dist-upgrader/binary-all/

cddirname=${0%\/*}
fullpath=$cddirname/$UPGRADER_DIR

# extrace the tar to a TMPDIR and run it from there
if [ ! -f $fullpath/$CODENAME.tar.gz ]; then
    echo "Could not find the upgrade application archive, exiting"
    exit 1
fi
```

I tried changing
```

cddirname=${0%\/*}
```

to
```

cddirname=/media/Ubuntu\ 7.10\ i386/
```

and saving that to /,

and when I run

```
gksu "sh /cdromupgrade"
```

I get

```
Could not find the upgrade application in the archive, exiting
```

Any suggestions?

---

### Post by ianmidd on 2007-10-18
No suggestions, but I'm having the exact same problem.

Still looking for a solution. 

I will post back if I get it going.

---

### Post by j.miller565 on 2007-10-18
Me too. I'm searching like a gibbon to try a get this working.

---

### Post by ianmidd on 2007-10-18
Still nothing....

Can anyone help us poor souls?

---

### Post by dabl on 2007-10-18
I think you're going at the hard way.  :(

See the check box under the green "Download" link?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check it, and then browse to a mirror that will work for you. Download the Alternate Install CD ISO image, check the md5sum, burn it, and use that to do your installation.

The servers seem real busy (congested) at this moment -- they'll probably be working better in a day or two.  :guitar:

---

### Post by ianmidd on 2007-10-18
I've burned the alternate cd iso from the official torrent.

I don't think it's an issue with the iso.

---

### Post by ianmidd on 2007-10-18
I think I got it going.

Here is what I did:

```
sudo umount /media/Ubuntu\ 7.10\ i386/ 
```

Then:

```
sudo mount /dev/cdrom /media/cdrom
```

As soon as I did that, the auto-run installer appeared on the screen.

---

### Post by DrClaw27 on 2007-10-18
Thanks that fixed my problem.:)

---

### Post by ianmidd on 2007-10-18
Yep, that did it!

I'm now up and running in Gusty!

---

### Post by irish_flu on 2007-10-19
Sweet, that fixed my issue (not successfully being able to run theupgrade script from the alt. cd)  as well.  thanks!

---

### Post by Lacrimstein on 2007-10-19
Didn't solve it for me. The CD gets mounted as /media/cdrom0. I can unmount it, but can't mount it back for some reason.... I will try use Nero to change the disc label (as far as I remember, there is an option like that)

---

### Post by Woozyerdaddee on 2007-10-21
OK.. I came here looking for the answer to the SAME problem, then I read the post about the "check box". Let me whine like a baby now: Waaaaa-waaaaaa They should have made the box more obvious and mentioned it a few more times, maybe add a babe in a bikini holding a sign that mentions it or SOMETHING! Most of us have learned to SCAN a page and click through them fast. Everyone who reads EVERY WORD on EVERY WEBSITE, please raise you hand...mmHHMM, I thought so :)

OK, I will go back into my cave and shut up now :)

---

### Post by ianmidd on 2007-10-25
> **Woozyerdaddee said:**
> OK.. I came here looking for the answer to the SAME problem, then I read the post about the "check box". Let me whine like a baby now: Waaaaa-waaaaaa They should have made the box more obvious and mentioned it a few more times, maybe add a babe in a bikini holding a sign that mentions it or SOMETHING! Most of us have learned to SCAN a page and click through them fast. Everyone who reads EVERY WORD on EVERY WEBSITE, please raise you hand...mmHHMM, I thought so :)

OK, I will go back into my cave and shut up now :)

I didn't see that post.  Where is it?

---

### Post by retsofbob on 2007-10-26
Another way around this problem is to delete the link \media\cdrom if you have one and create a new one pointing to '/media/Ubuntu 7.10 i386/'.  Then you can run cdromupgrade.  Here's how I did it:

[LIST=1]
[*]gksudo nautilus
[*]browse to /media
[*]if you have a cdrom link already (I did) then delete it.
[*]right click on 'Ubuntu 7.10 i386'
[*]create link called cdrom
[*]browse cdrom and run cdromupgrade
[/LIST]

Good Luck.

Bob

---

### Post by jdarias on 2007-10-26
No luck for me.
I've tried all solutions, and when cdromupgrade starts, soon fails with this:
> No se ha podido calcular la actualización

Ha ocurrido un problema irresoluble mientras se calculaba la actualización.

Por favor, notifique este fallo sobre el paquete «update-manager» e incluya los archivos de /var/log/dist-upgrade/ en el informe.
sorry for non-english :(

---

### Post by Endolith on 2008-04-24
The CD or ISO should be mounted in /media/cdrom0 and then you run it with the command ```
/media/cdrom/cdromupgrade
```  This is the only command that works.  /media/cdrom0/cdromupgrade will not work, for instance, even if that's where the file actually is.  You need to use the link.

---

