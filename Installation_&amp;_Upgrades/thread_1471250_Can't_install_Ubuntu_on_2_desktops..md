---
title: "Can't install Ubuntu on 2 desktops."
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by pabloda on 2010-05-03
Ok, I've been trying to install Ubuntu on a Compaq desktop (Pentium 4 @2.80Ghz, 256mb ram, Intel extreme graphics.) and on a generic desktop (Pentium 3 with 256mb ram.) No luck with 9.04, so when 10.04 went out I tried it with no luck either.

Tried to boot from a flash drive using uNetbootin, no luck. Tried from a DVD and choose the installer, then a message appears telling that the installer had a problem and the login screen appears, but can't login with login:ubuntu password:none.

Any help?
P.D. also tried Linux Mint 8, no luck either.

---

### Post by amsterdamharu on 2010-05-03
Can you boot from CD and run "try ubuntu" option also known as the live CD?

---

### Post by P4man on 2010-05-03
Make sure your download is not corrupted. Run the md5 checksum on the ISO and/or run the cd verification from the cd menu (or usb).

Secondly, 256Mb is minimum minimorum (I actually think its below minimum specs for a livecd). Chances are onboard video is reducing the amount even further. Do not run the "try ubuntu without installing", it requires more ram. You might be able to install it choosing install ubuntu now. or by using the alternate cd.

Even so, you probably want a different distribution if you only have 256 Mb. I would suggest looking at pclinuxos. Maybe xubuntu, but ubuntu (gnome) will not be pleasant.

edit look here:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You are well below minimum specs for ubuntu. You are right on the minimum specs for xubuntu (alternate cd recommended). I still stand by my suggestion of trying a more lightweight distribution.

edit bis: seems pclinuxos has taken on quite some fat as well, requiring 512Mb and 1gb recommended. Ouch! I remember running pclinuxos 2007 (I think) with 128 Mb! So change that suggestion to [http://www.puppylinux.org/](http://www.puppylinux.org/) or [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by techunit on 2010-05-03
Try using the alternate install .iso it uses a text based installer it will be a little bit harder.

---

### Post by sanderd17 on 2010-05-03
256mb is not so high, maybe it will run but it'll be difficult to try a life cd with it. Can you try a lighter distro? Like Xubuntu or Lubuntu?

Also at login, I believe you should login as nothing (just hitting enter).

EDIT: Linux Mint will definatly be a dead end, that uses more resources than ubuntu does

---

### Post by techunit on 2010-05-03
I would recommend that you try xubuntu... I think that it will work

---

### Post by pabloda on 2010-05-03
Ok, thank you all, i'll try Lubuntu and post how it went.
EDIT: While Lubuntu is downloading, i'll try UNR. Who knows...

EDIT 2: No go with UNR 10.04, nor with ChromeOS Flow

---

### Post by techunit on 2010-05-03
Good luck Xubuntu has more of the feel of ubuntu though.

---

### Post by plus2plus on 2010-05-03
A video tutorial [Ubuntu Desktop in Virtual PC Part 2]("http://www.youtube.com/watch?v=S3MZY6fwV2c")

---

### Post by techunit on 2010-05-03
> **plus2plus said:**
> A video tutorial [Ubu]("http://www.youtube.com/watch?v=S3MZY6fwV2c")[ntu Desktop in Virtual PC Part 2]("http://www.youtube.com/watch?v=S3MZY6fwV2c")


relavence please? we aren't talking about running ubuntu in a virtual machine.

---

### Post by techunit on 2010-05-03
well please post you opinion of lubuntu if you have had any luck with it. other than that I guess you could try ubuntu 8.04 that will run fine I think but it is a couple of years old.

---

### Post by amsterdamharu on 2010-05-04
> Do not run the "try ubuntu without installing", it requires more ram. You might be able to install it choosing install ubuntu now. or by using the alternate cd.

That is strange, the live cd iso worked in VirtualBox using 194MB of memory why would it not run on a computer from a CD?

I agree with the alternate, it will solve some issues you might have with your videocard. You might try ubuntu minimal and to only install commandline ubuntu. From there use commands to install a gui and software. You need an internet connection for it to work though.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

> After the base system installed, log in, and type "sudo tasksel" to select the system to install. 

---

### Post by P4man on 2010-05-04
> **amsterdamharu said:**
> That is strange, the live cd iso worked in VirtualBox using 194MB of memory why would it not run on a computer from a CD?

Did the VM have access to a (virtual) drive with a swap partition? A live cd will swapon if it can. try booting it with no virtual harddisk.

Also the VM may not require all the drivers and stuff that an actual physical PC has, as you may not have any USB devices or even controllers, nor as many peripherals, network cards, only a vesa driver etc.

Im not saying a livecd will definitely not work on any machine with <256 Mb, but I wouldnt count on it working.

---

### Post by amsterdamharu on 2010-05-04
@p4man
Ok, that makes sense, haven't tried it without virtual harddisk. The op wasn't really clear on what failed I guessed it would be video driver so next advice is alternate which was already given. 

Since the op's computer is low on memory an ubuntu minimal might work even better but then the computer needs a working internet connection. If the computer is missing an Internet connection then there are ways of doing it but it's complicated.

---

### Post by pabloda on 2010-05-04
:confused: Guys... no luck with Lubuntu. And this is starting to annoy me a lil'. Last try, Xubuntu.

---

### Post by techunit on 2010-05-04
Well if your system cant run lubuntu then it won't run xubuntu. But I think there is probably a different reason you can run the live cds...

---

### Post by pabloda on 2010-05-04
> **techunit said:**
> Well if your system cant run lubuntu then it won't run xubuntu. But I think there is probably a different reason you can run the live cds...

Well then, I'll try Lubuntu alternate CD. :?
AND apparently there isn't one-.-

---

### Post by techunit on 2010-05-04
I have run used ubuntu 8.04 on a similar system

---

### Post by P4man on 2010-05-04
are you sure you are burning correct cds? Even if the machines are unable to run the live session, you should be able to run the "check this cd for errors" from the menu. Does that at least work? If it doesnt, you got a different problem

If that does work, I suggest you look at puppylinux  or if you want to make those machines faster than fast, [slitaz]("http://www.slitaz.org/en/"). Yes they are rather basic distro's (slitaz more so than puppy), but they have firefox, quite useable office and email suites and on a somewhat modern machine I tried slitaz and it would boot in like 5 seconds.

---

### Post by techunit on 2010-05-04
> **P4man said:**
> are you sure you are burning correct cds? Even if the machines are unable to run the live session, you should be able to run the "check this cd for errors" from the menu. Does that at least work? If it doesnt, you got a different problem

If that does work, I suggest you look at puppylinux  or if you want to make those machines faster than fast, [slitaz]("http://www.slitaz.org/en/"). Yes they are rather basic distro's (slitaz more so than puppy), but they have firefox, quite useable office and email suites and on a somewhat modern machine I tried slitaz and it would boot in like 5 seconds.


I agree how are you buring the cds? But I don't know how experienced you are with linux but this got me for a while. I recommend that you try using imgBurn if you have access to a windows computer.

Sorry if you take offense from this but I really can't tell how much experience you have with linux and live cds

---

### Post by pabloda on 2010-05-05
> **techunit said:**
> I agree how are you buring the cds? But I don't know how experienced you are with linux but this got me for a while. I recommend that you try using imgBurn if you have access to a windows computer.

Sorry if you take offense from this but I really can't tell how much experience you have with linux and live cds

Yup I burn them with imgBurn, the same as I did as my Windows and other Linux distros, also I tried from USB flash drives with uNetbootin, no luck.


-I'll try 8.04 ](*,)

---

### Post by techunit on 2010-05-05
Are you making sure to set the bios to boot from the CD first?

---

### Post by pabloda on 2010-05-05
> **techunit said:**
> Are you making sure to set the bios to boot from the CD first?

Yes I am. It actually boots from the CD/USB but when it is loading, the screen becomes black on every single distro i've tried.

BTW just telling, I use PloB Boot manager to boot from USB, i doubt this is the reason of my problem, since i've used it in other computers with good results.

---

### Post by P4man on 2010-05-05
pabloda, do you get the initial menu where you can chose between installing ubuntu, and trying it without changes, and checking the cd for errors, or not even that?

---

### Post by pabloda on 2010-05-05
> **P4man said:**
> pabloda, do you get the initial menu where you can chose between installing ubuntu, and trying it without changes, and checking the cd for errors, or not even that?

yes i get to the menu, i've tried the different options with no luck either. right now i'm downloading ubuntu 8.04, hopefully it will work.

---

### Post by pabloda on 2010-05-05
> **P4man said:**
> pabloda, do you get the initial menu where you can chose between installing ubuntu, and trying it without changes, and checking the cd for errors, or not even that?

yes i get to the menu, i've tried the different options with no luck either. right now i'm downloading ubuntu 8.04, hopefully it will work.

also, memtest went fine. haven't tried checking the cd, but i really don't think the cd is the problem.

---

### Post by pabloda on 2010-05-05
Guys, you are going to hate me :S.
I tried on another monitor and guess what? yes, apparently it worked-.-

i'm trying all the distros i've tried before to see how they go.

Jolicloud pre-final starts the live cd but VERY VERY SLOW

EDIT: I was able to install 10.04 but it won't load after the install. 8.04 was AMAZING in the live session (even some compiz effects were enabled) but after install, i logged in and the background was frozen.
So I'm installing Windows :(
But i will try dual-boot with debian later

---

### Post by techunit on 2010-05-09
We don't hate people because of funky hardware. Debian is a decent distro I hope you get everything worked out.

---

### Post by techunit on 2010-05-09
Please note that Debian is not a live cd unless you go to a specific source hope this helps.... Just search debian live cd

---

### Post by jeditalian on 2010-05-23
i can only imagine how sluggish your computer runs anything with a processor so good, yet so little ram. upgrading your ram should be pretty affordable nowadays, provided you buy online and not from say, bestbuy

---

### Post by P4man on 2010-05-23
Here is another ubuntu based distro that might be worth looking at
[http://peppermintos.com/](http://peppermintos.com/)

apparently boots in just 85Mb memory

---

