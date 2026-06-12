---
title: "How can I execute &quot;apt-get install&quot; without a ubuntu DVD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by chrysler on 2007-05-05
We know that we must prepare the ubuntu DVD whenever we install something which they're in the ubuntu DVD, even if we connected to Internet. It's inconvenient, right? Especially when I bring my laptop to somewhere, I forgot bringing the ubuntu DVD.

I wish to copy the DVD content to my hard disk, and then I can install the programs without the ubuntu DVD.

My solution is mount the ubuntu DVD iso file as /media/cdrom now. But I feel that it's still inconvenient.

Can I copy the files in ubuntu DVD to my hard disk and then install the packages without preparing the ubuntu DVD forever? How can I do? How to modify sources.list file?:(

---

### Post by aysiu on 2007-05-05
Paste the following commands into [the terminal](http://www.psychocats.net/ubuntu/terminal).

Create an ISO of the DVD in some place--say, ~/.repositories/ubuntu.iso: ```
mkdir ~/.repositories
sudo umount /dev/cdrom
dd if=/dev/cdrom of=ubuntu.iso bs=1024
mv ubuntu.iso ~/.repositories/
``` Then mount the ISO: ```
sudo mkdir /media/repositories
sudo modprobe loop
sudo mount ~/.repositories/ubuntu.iso /media/repositories -t iso9660 -o loop
```

Finally, make the DVD ISO your source: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
``` Add in this line: ```
deb file::///media/repositories/ *dapper* main restricted
``` Then save (Control-X, Y, Enter) and update ```
sudo apt-get update
``` Not sure what version DVD you have. I just used *dapper* as an example. You can substitute in *edgy* if you're using 6.10 or *feisty* if you're using 7.04.

You can also find another, similar tutorial here:
[How To Automatically Mount An Ubuntu CD Image And Use It As An Additional Software Repository](http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/)

---

### Post by imon9 on 2007-05-05
simpler way;
go to "synaptic">setting>respositories..
then  uncheck the CD/DVD as your source

DONE

---

### Post by aysiu on 2007-05-05
> **imon9 said:**
> simpler way;
go to "synaptic">setting>respositories..
then  uncheck the CD/DVD as your source

DONE
That doesn't really answer the last question: > Can I copy the files in ubuntu DVD to my hard disk and then install the packages without preparing the ubuntu DVD forever? How can I do? How to modify sources.list file?

---

