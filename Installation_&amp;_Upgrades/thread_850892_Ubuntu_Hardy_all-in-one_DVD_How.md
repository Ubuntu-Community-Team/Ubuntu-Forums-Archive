---
title: "Ubuntu Hardy all-in-one DVD: How?"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by prshah on 2008-07-06
Hello,

I'd like to make an all-in-one-live-dvd of various Ubuntu distros, eg. Ubuntu, Kubuntu, Xubuntu.

I have a blank system, on which I plan to install all three. No sharing of /home partition and/or files. Once all three are setup and OK, I plan to use remastersys to create a master dvd image.

I then wish to use GRUB (on the dvd) to boot the selected live distro.

I have no knowledge of remastersys except that I know it can be used to xfer an existing install to live CD.

I don't care whether or not there is any interaction between the multiple distros on the DVD.

Can this be done? Or is there a simpler way? Any and all suggestions welcome.

For your reference when posting advice, commands, links, etc: my tech level: intermediate-high.

I'd also like to include the server-install if it is not too difficult, as well as the 64-bit versions (My current blank system can handle 64 bit).

---

### Post by prshah on 2008-07-12
(First-time-ever-)bump?

---

### Post by charliebrownau on 2008-07-12
Sounds like a great idea !

Love to see an Ubuntu 8.04.1 AIO DVDR disc
with Ubuntu 8.04.1, Kbuntu 8.04.1 , Uubuntu EEE 8.04
and extra deb/ubuntu files instead of using internet
apt repositories.

---

### Post by charliebrownau on 2008-08-18
Still no response, thats a shame

---

### Post by Israeru on 2008-08-18
I am tryng to make something similar but not only with ubuntu...
[http://ubuntuforums.org/showthread.php?t=892598](http://ubuntuforums.org/showthread.php?t=892598)

---

### Post by prshah on 2008-08-18
> **Israeru said:**
> I am tryng to make something similar but not only with ubuntu...
[http://ubuntuforums.org/showthread.php?t=892598](http://ubuntuforums.org/showthread.php?t=892598)

Thanks, your link gave me the clue that I need. I've been reading up for the past 4 hours on isolinux, etc etc, and I believe that I'm nearly ready to attempt this. For those who are interested, I will keep a running commentary here.

---

### Post by lekidos on 2008-08-18
I was at Barns and Nobel bookstore today, and picked up an Ubuntu 8.0.4 magizne, brought by Linux Identity, and it thus contained a DVD of all versions of Ubuntu (Cubuntu Mythbuntu and Kubuntu incl.) 32 bit and 64bit on a separate DVD.

---

### Post by Israeru on 2008-08-21
Hello Lekidos

Can you email us the initrd.gz and the and post the isolinux.cfg of that dvd?
It´s the part that boot linux Ubuntu.

The files are in /casper carpet or search it in the DVD.

Can you post the directory structure and the contents of your dvd?

ls -lah in the root of the dvd.

Greetings.

---

### Post by prshah on 2008-09-22
Well:

I've downloaded K,X,Ubuntu 8.04.1 iso images.

I've mounted these images, copied the files, setup isolinux/isolinux.cfg.

When I burn the image to DVD and try to boot off it, I get an error> ISOLINUX 3.53 Debian-2007-12-11 isolinux: Image checksum error, sorry...

So I started off again to first get it working with a single distro, Ubuntu 8.04.1.

First, I mounted the ISO using gmount-iso and copied over all the files```

cd ~/downloads/test
cp -R -p -v /media/isomount/* .
sudo cp -R -p -v /media/isomount/.disk .

```

Then, I ran an md5 check to ensure that the files are copied OK```
md5sum -c md5sum.txt | grep -i fail
```

Then, I created the CD image with```

mkisofs -J -R -l -r -V "Ubuntu 8.04.1 i3" -o ~/downloads/ubuntuaio.iso -b isolinux/isolinux.bin -no-emul-boot -boot-load-size 4 . 

```

Note that I've kept the volume ID the same as the original disk image.

When I boot this image, either in Virtual Box, or by burning it to CD, I get the same error as mentioned before.

I mount the custom CD image manually, and run the md5 check again. and there are no errors (All OK).

The original image mounts and boots perfectly in Virtual Box.

The closest google result on this error revealed that some outdated BIOSes don't work, so I burnt it on a CD and tried it on various machines; in all, the original CD worked fine, my (custom) CD did not.

I'm using a fully updated 32bit ubuntu 8.04.1 installation.

Any suggestions / tips?

---

### Post by prshah on 2008-09-22
OK, Problem cleared, will post details shortly.

---

### Post by charliebrownau on 2008-10-30
Sounds like an interesting project .

Did you have to get permission from the different Linux teams to do it ?

I Would still like to see an Ubuntu AIO DVDR 
even if its an 8 gig ISO

---

### Post by prshah on 2009-10-22
> **prshah said:**
> 
I'd like to make an all-in-one-live-dvd of various Ubuntu distros, eg. Ubuntu, Kubuntu, Xubuntu.

Hey, I did it! Thanks to various other posts on the forums; all details, including kudos, instructions, screenshots, videos: [http://prshah.blogspot.com/2009/10/ive-been-trying-to-make-ubuntu-all-in.html](http://prshah.blogspot.com/2009/10/ive-been-trying-to-make-ubuntu-all-in.html)

---

### Post by ranjank on 2010-05-07
How can I make  5 Os  AIO Live DVD ? Please give step by step method (Ubuntu 10.04,Kubuntu 10.04,xubuntu 10.04 , Lubuntu 10.04 ,Mythbuntu 10.04) .

---

### Post by Israeru on 2010-05-09
Interesting, uhm a question do you use the same initrd for all the ubuntus versions?

---

