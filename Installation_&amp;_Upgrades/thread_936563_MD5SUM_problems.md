---
title: "MD5SUM problems"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Ztruker on 2008-10-02
I am seeing MD5SUM mismatches for: 

ubuntu-8.04.1-alternate-i386.iso 732,446,720 bytes
14356a8daf0234685702f1a7c8298b77 MD5SUM on web site
bbd21ded02c06b41c59485266833937a md5sum output under Win XP

ubuntu-8.04.1-desktop-i386.iso  728,221,696 bytes
cde82e1566ad8a88e36138853c195b5f MD5SUM on web site
c69e34e92d5402d1b87e6babc739f774 md5sum output under Win XP

I used Free Download Manager under Win XP Pro+SP3 to download both iso images and I downloaded from:

[United States Gigenet (North America)]("http://mirrors.gigenet.com/ubuntu/")

I'm using md5sum.exe from a Unixtools port.

Any way to tell if I'm having download problems or is my md5sum.exe no good? Any suggestions for another md5sum generator?

Thanks, Rich

---

### Post by iaculallad on 2008-10-02
Try getting your ISO image file in this [site]("http://cdimage.ubuntu.com/hardy/"). File corruption must have been caused by transmission error. Try the md5 utility w/c comes with sleuthkit.

```
sudo apt-get install sleuthkit
```

```
md5 filename.iso
```

EDIT: All md5 computation utility uses the same algorithm on computing the hash. Just probably be a transmission error.

---

### Post by Ztruker on 2008-10-02
Downloaded again from same site using the Free Download Manager. Used a different md5 gen program (DigestIT 2004) and got the exact same hash that I did with md5sum.exe.

I just started a download from the link you gave me. Will see how that works out. It's very slow compared to the Gigebit site though, looks like it will take an hour or more so I'll let it run over night.

I'll post results tomorrow.  Thanks

Rich

**[COLOR="Red"]Edit:[/COLOR]** I don't have Linux installed so can't use **sudo apt-get install sleuthkit**

[COLOR="Red"]**Edit#2**[/COLOR]: The reason it was so slow is I downloaded the DVD image instead of the CD image!

---

### Post by craagathor on 2008-10-03
c69e34e92d5402d1b87e6babc739f774 is what i got after a checking the image hash on xp. 

[http://whyamistilltyping.wordpress.com/2008/04/24/ubuntu-804-md5-checksums/](http://whyamistilltyping.wordpress.com/2008/04/24/ubuntu-804-md5-checksums/)

the same as at this site

---

### Post by grim4593 on 2008-10-03
If you want to make sure your download is correct, and so you don't have to redownload the entire thing if just a few parts are messed up, download the torrent file, rename the iso if required (make sure you have matching versions though), and then it will check it for hash errors. If it finds one, it will redownload the required pieces and you will have a whole iso.

---

### Post by Ztruker on 2008-10-03
So from craagathor's post, the md5 hash I have is correct then. I must have read the wrong file on [Gigenet]("http://mirrors.gigenet.com/ubuntu/8.04.1/").

Thanks, Rich

---

