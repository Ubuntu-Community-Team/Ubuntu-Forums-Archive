---
title: "netboot installation fails"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Cletus Van Damme on 2008-06-10
Hello,

I have currently set up a preseeded netboot installation for Ubuntu 8.04 Hardy and it has worked fairly well for a week or two.

Now mysteriously enough the installer fails with the error message "Failed to load installer component - Loading libntfs-3g23-udeb failed for unknown reasons. Aborting." in the download installer components phase.

I have tried this several other mirrors, with and without preseed and it always fails the same way. I even enabled BOOT_DEBUG=2 but the installation log does not give out any additional information on this matter.

---

### Post by jlgreer on 2008-06-10
I'm experiencing the same problem - netbooting Hardy has worked for a month until within this week (just noticed it today).  Attaching syslog and hardware summary.

---

### Post by Brian Zachary on 2008-06-10
Just confirming that this is a problem I'm experiencing for the first time today as well, during a preseeded netboot install of 8.04 from a local mirror (itself a mirror of [www.gtlib.gatech.edu/pub/ubuntu](www.gtlib.gatech.edu/pub/ubuntu)).

---

### Post by avtolle on 2008-06-10
Just wondering whether the recent kernel upgrades have anything to do with the problems you folks are experiencing. My question, such as it is, was suggested by one of the questions and answers of the Q and A part of the following:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by jlgreer on 2008-06-10
Thanks, avtolle!  Unfortunately, it's looking to me as though the pxelinux components of netboot were updated today, but the netboot kernel and ramdisk have remained the same since the Hardy launch, so I'm not sure how to go about getting netboot in agreement with my local mirror:
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

The Hardy netboot tarball at the page you listed earlier is all from April too.

How difficult would it be to build my own updated netboot kernel (and ramdisk) - am I correct in assuming that's just a vanilla kernel with a wide array of network/disk support?  Would it be better to just wait for an update to come down the stream?

---

### Post by avtolle on 2008-06-10
You have exceeded my knowledge with your penultimate question, there jlgreer, thus I'd wait for an update to come down stream. Just my 2 cents.

---

### Post by eci_souji on 2008-06-10
Hey everyone, I'm having the exact same issue with my amd64 based installations.  We do use a custom kernel and have been perfectly fine until today.  I'm guessing this is something odd with that specific package and have filed a bug report at [https://bugs.launchpad.net/ubuntu/+bug/238974]("https://bugs.launchpad.net/ubuntu/+bug/238974") 

Has anyone managed to do a succesful network install today?  :(

- E

---

### Post by eci_souji on 2008-06-10
So if you have console access you can get past this error by selecting <Continue>, <Continue>, Download Installer Components, <Continue>.  Not a solution but if you need boxes rolled out like I do it seems to make it :\

- E

---

### Post by jlgreer on 2008-06-10
Thank you, eci_souji!  That appears to be working for me too.

---

### Post by theatrus on 2008-06-10
Bitten by the same problem :(

---

### Post by Xyem on 2008-06-10
I am too experiencing this problem, although it worked fine less than 12 hours ago.. perhaps the approx cache on my server hadn't been "hit" yet..

eci_souji's suggestion also seems to work but I don't put any faith in things when it just "works the next time" when nothing has changed..

I'll await further news as I am trying to install 8.04 on my USB stick.

---

### Post by Cletus Van Damme on 2008-06-11
Is it possible to avoid loading this particular troublesome module with some kind of preseed parameter? I have no need for NTFS support for my unattended setup which consists of nuking the first available drive.

---

### Post by psypointer on 2008-06-11
the same problem here and no idea how to solve it. i just reinstalled my netboot image but that did not help. maybe the ntfs3g lib is to modern for 2.6.24-16 (actual versoin in the repo is 2.6.24-18).

if anyone has an idea how to solve it please write it in here..

psypointer

---

### Post by stump138 on 2008-06-11
I'm also having this on netboots, however, I can accept the error and continue with no issues like others in this thread.

---

### Post by psypointer on 2008-06-11
jeah thats right, you can continue manually. but the preseed scripts doesn't work anymore after this error :(

---

### Post by cjwatson on 2008-06-11
This is [bug 234486]("https://bugs.launchpad.net/ubuntu/+source/net-retriever/+bug/234486"), and should be fixed in hardy-proposed. Please try the [hardy-proposed netboot images]("http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/") and verify that it's really fixed.

---

### Post by eci_souji on 2008-06-11
Grabbed the new amd64 initrd.gz and install went perfectly.  Thanks for the quick fix! :KS


- E

---

### Post by cjwatson on 2008-06-11
Oh, in case you don't see it on the bug report, for the time being you need to boot with "apt-setup/proposed=true" on the kernel command line in order to use these images. (That will go away once the kernel they use gets into hardy-updates.)

---

### Post by psypointer on 2008-06-12
installation works perfect with apt-setup/proposed=true but it ignores my preseed_late command now. preseed_early works perfectly.

edit: it works

---

### Post by Xyem on 2008-06-12
I don't want to install with proposed in case it pulls in other ( unstable? ) things. I'll test this in QEMU later though, even though it sounds fixed :)

How long would this take to get into the updates?

Awesome work with, as expected ( to be honest ), a fix within 48 hours. Hopefully I can do my USB install soon :)

---

### Post by Xyem on 2008-06-13
Sorry for the double post, thought it might be good to bump this topic.

I just tried the mini.iso that was giving me the error as before but this time, the package was different.

> Loading kickseed-common failed for unknown reasons. Aborting

Do I need to get a replacement mini.iso?

---

### Post by cjwatson on 2008-06-13
Yes, the exact nature of the error will drift depending on what else lands in -updates. As I said, it wasn't a problem with ntfs-3g as such.

You definitely need to get a replacement mini.iso, and I'm afraid that for now you do have to use -proposed (and apt-setup/proposed=true) or it simply won't work. This will get into -updates in time for the point release in early July, though.

---

### Post by Xyem on 2008-06-13
Guess I'll be doing a minimal install from CD and updating then, I don't have the patience to wait until July to install Ubuntu on my portable storage :P

Thanks for the feedback

---

### Post by yuunagi on 2008-06-17
Although we have recieved the following message,
If we keep going, Installation is completed normally. 

(Quote message:
Loading kickseed-common failed for unknown reasons. Aborting) 

We added some options of apt-setup/proposed=true,
but, the situation did not change.

So is it okay for us to igonore the above message?

---

### Post by cjwatson on 2008-06-17
That's the same type of error as before. No, you can't ignore it. Please confirm the URL from which you downloaded the installer image; the one in hardy **will not work** and you have to use hardy-proposed.

---

### Post by mcsuperhouse on 2008-06-19
[You definitely need to get a replacement mini.iso, and I'm afraid that for now you do have to use -proposed (and apt-setup/proposed=true) or it simply won't work. This will get into -updates in time for the point release in early July, though.[/QUOTE]

I also get that 

"loading kickseed-common failed for unkown reasons. aborting."

What iso must we use then cos i downloaded mine wed 18 june, late afternoon (CAT) - and i get the same errors -what must I do ... what is this apt-setup... I only know how to run the cud -there is no option for a command line console.. So what must i do -has the iso been updated since i downloaded it or what else must I do?

---

### Post by Xyem on 2008-06-19
**Note: This was entirely from my memory which _isn't very good_ :P Please skip to the edited section at the bottom.**

Did you download the mini.iso from: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/)

You should be presented with a menu during the boot up ( if I recall correctly ) and one of the function keys ( I think it might be F6 ) will bring up a little box in the lower right corner. You have to add
> apt-setup/proposed=trueto the end.

-=-=- EDIT -=-=-

To do a netboot install, download the [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/mini.iso") and as a boot parameter, type in:

> apt-setup/proposed=true

Attached are screen-shots that show an errorless minimal install from the netboot image.

---

### Post by cjwatson on 2008-06-19
You need to use:

[http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/mini.iso)

The one in /dists/hardy/ will not work.

---

### Post by mcsuperhouse on 2008-06-19
> **Xyem said:**
> **Note: This is entirely from my memory which _isn't very good_ :P I shall correct/confirm when I get home ( next 20 minutes ).**

Did you download the mini.iso from: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/)

You should be presented with a menu during the boot up ( if I recall correctly ) and one of the function keys ( I think it might be F6 ) will bring up a little box in the lower right corner. You have to add

to the end.

I was trying to do a kubuntu install for my 128MB laptop 
but then I used [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso)
I gues that it the same - When was the bug fixed cos like i said i downloaded it yest aft (CAT)

---

### Post by Xyem on 2008-06-19
If you follow the instructions on my previous post ( which I have now edited ) and install a minimal system, you can then install the xubuntu-desktop package to get an Xubuntu install.

> sudo aptitude install xubuntu-desktop

---

### Post by mcsuperhouse on 2008-06-19
> **Xyem said:**
> If you follow the instructions on my previous post ( which I have now edited ) and install a minimal system, you can then install the xubuntu-desktop package to get an Xubuntu install.

Ok I get the first code line right - cli apt-setup/proposed=true
but then after that I get the same message 
"loading kickseed-common failed for unkown reasons. aborting."

not If I am supposed to type those other codes in before somewhere or if my ISO is buggered.. any idea?

---

### Post by Xyem on 2008-06-19
Can you post the md5sum of your ISO?

---

### Post by cjwatson on 2008-06-20
/dists/hardy/ is *NOT* the same as /dists/hardy-proposed/ or /dists/hardy-updates/.

---

### Post by Xyem on 2008-07-14
I just saw that the point release is out. Can someone confirm that the mini.iso here ( [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso) ) is the one I should be downloading?

It might be a good idea to change the link on [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) as it still points to the old, "broken" mini.iso..

---

### Post by cjwatson on 2008-07-15
Yes, that is the correct link. I've changed the help wiki, thanks.

---

### Post by stump138 on 2008-07-18
Can anyone else confirm failures of netboot installation either after tasksel with the error:

" linux-headers-generic: Depends: linux-headers-2.6.24-19-generic but it is not going to be installed"

I'm getting this error whether I use archive.ubuntu.com for the repo or a local apt-cacher repo.

I've also tried the proposed netboot image as well as the one located in main and still get the same errors.

---

### Post by Xyem on 2008-07-18
I'm not sure if this is of any help to you but I am not seeing this error ( having installed from the hardy-updates mini.iso onto my laptop ) going through my local approx cache ( which is on another machine ).

---

### Post by stump138 on 2008-07-18
thanks, think I got this one solved for now by adding:

```

apt-setup/proposed=true

```
to the kernel append in pxelinux.cfg/default

This is solving the issue for now, seems not all of the kernel 2.6.24-19 isn't in the main repos yet (just a guess) because using the proposed repos solves the issue.

---

### Post by s7726 on 2008-11-26
I'm getting the same error with a net install of Intrepid 8.10. The <Continue>, <Continue>, Download Installer Components, <Continue> solution seems to be making it work.

Any Idea on what the root problem is? I got the files for the netboot and everything from the alternate install iso I downloaded from the get ubuntu site.

---

