---
title: "installing from a live cd"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by helphelp on 2011-10-17
Hello
I'm trying to install ubuntu from a live cd without any luck.
The cd starts and after the rectangle and circle logo it stops.
The message is saying  {  unexpected exit with ststus 0x0009  }

firewire_core: created device fw0: GUID 00c09f0000a95a54,  S400

Please help if you can
thanks

---

### Post by zvacet on 2011-10-17
Check md5sum and check disc for errors.You can find guide [here.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by ajsoulmate on 2011-10-17
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by nzjethro on 2011-10-17
Can you run Live, as opposed to trying to install?

---

### Post by helphelp on 2011-10-18
> **zvacet said:**
> Check md5sum and check disc for errors.You can find guide [here.]("https://help.ubuntu.com/community/BurningIsoHowto")
  Thanks but the cd is ok .It's been used to install ubuntu a few times without any problem.

---

### Post by helphelp on 2011-10-18
> **ajsoulmate said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Thanks but the cd has been used a few times without any problem.

---

### Post by Bmonsterboy on 2011-10-18
> **helphelp said:**
> Thanks but the cd is ok .It's been used to install ubuntu a few times without any problem.

Yeah, but it's more than likely that it may have been scratched or damaged. You have to check the disk for errors, even though it may have worked before, even though it may work right now on another computer, it still may be faulty.

---

### Post by helphelp on 2011-10-18
> **nzjethro said:**
> Can you run Live, as opposed to trying to install?
Thanks but it doesn't let me run it live.

---

### Post by helphelp on 2011-10-18
> **Bmonsterboy said:**
> Yeah, but it's more than likely that it may have been scratched or damaged. You have to check the disk for errors, even though it may have worked before, even though it may work right now on another computer, it still may be faulty.
I see .  How do i go about checking it for errors?

---

### Post by Bmonsterboy on 2011-10-18
> **zvacet said:**
> Check md5sum and check disc for errors.You can find guide [here.]("https://help.ubuntu.com/community/BurningIsoHowto")

That's how.

---

### Post by helphelp on 2011-10-19
> **Bmonsterboy said:**
> That's how.
 Hi,
I downloaded ubuntu from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
I then typed  cd Downloads into terminal followed by md5sum ubuntu-11.10-desktop-i386.iso
The number i got was c396dd0f97bd122691bdb92d7e68fde5
I then went to [http://releases.ubuntu.com/oneiric/MD5SUMS](http://releases.ubuntu.com/oneiric/MD5SUMS)
These were the numbers i got
5e427f31e6b10315ada74094e8d5d483 *ubuntu-11.10-alternate-amd64.iso
24da873c870d6a3dbfc17390dda52eb8 *ubuntu-11.10-alternate-i386.iso  62fb5d750c30a27a26d01c5f3d8df459 *ubuntu-11.10-desktop-amd64.iso
c396dd0f97bd122691bdb92d7e68fde5 *ubuntu-11.10-desktop-i386.iso                                                                                                     The number is the same as the fourth line.
I then used the burn image iso file option in Xfburn to burn it to disk at a low speed
Have i done this right?  because when i tried to install it was ok untill  i had to put in details  like where in the world i was { time zone}
The picture and other information  was unreadable.

I tried the option to just try ubuntu without installing and that was ok untill it froze .

---

### Post by vicshrike on 2011-10-19
Try google with "  unexpected exit with ststus 0x0009", it has happened to others earlier, good luck!

---

### Post by oldfred on 2011-10-19
What video card? this works for some.

To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

---

### Post by helphelp on 2011-10-20
> **oldfred said:**
> What video card? this works for some.

To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.



TOPMAN    No need to burn any cd's  ,installed from my original ubuntu disc
many thanks
My computer finished  installing  and after the  restart all i get is a small  flashing light at the top left of the screen.
I tried recovery mode and the last line says    eth0: no IPv6 routers present

---

### Post by oldfred on 2011-10-20
You usually need nomodeset on first boot until you install proprietary drivers.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

I have nVidia which you then can install. Not sure about others.

---

### Post by helphelp on 2011-10-20
> **oldfred said:**
> You usually need nomodeset on first boot until you install proprietary drivers.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

I have nVidia which you then can install. Not sure about others.
  Done that
cheers

---

