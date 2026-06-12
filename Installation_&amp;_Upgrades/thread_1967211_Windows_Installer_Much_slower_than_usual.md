---
title: "Windows Installer: Much slower than usual"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by danielgrosvenor on 2012-04-27
As I'm not an expert when it comes to partitioning (I'm never too sure what to do with SWAP drives, etc) I decided to try the Ubuntu Windows Installer to achieve my latest dual-boot.

The install went smoothly, and I allocated the recommended 18GB to the Ubuntu partition. Despite having run all updates, I'm still noticing that Ubuntu is running significantly slower than any of my previous installs (have in the past run various Ubuntu and Kubuntu versions on this machine and they've been nice and speedy). Both booting up and loading programs takes a noticeably longer time than it should.

Now, I know nothing about how the Windows Installer works. Would it have allocated a reasonable SWAP partition? Or does it do some mysterious 'Windows thing'? I'm wondering whether there's a way to speed things up, or whether I'd be better simply using Gparted to shrink my Windows partition, create an ext4 and a SWAP partition *(how big should that be?? :S )* and reinstall Ubuntu the old fashioned way from a CD.


I have a Dell Inspiron 1307 laptop with a pretty reasonable spec (64 bit, core 2 duo, 4 gigs DDR3 RAM) so, unless 12.04 is significantly more demanding than Oneiric Ocelot, hardware shouldn't be an issue.

---

### Post by Rubi1200 on 2012-04-28
In general, it is preferable to install Linux directly to the drive if you intend using it long-term.

That said, the specifications look good and you should not normally be experiencing such performance issues with Wubi (at least not to the extent you are reporting).

I suggest checking out this great blog for possible further information:
[http://ubuntu-with-wubi.blogspot.com/](http://ubuntu-with-wubi.blogspot.com/)

---

