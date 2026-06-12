---
title: "Secure Boot stops Ubuntu usb from booting"
date: 2023-02-19
forum: Installation &amp; Upgrades
---

### Post by donald187 on 2023-02-19
I have a Dell Inspiron 3910.  I've been on Ubuntu 22.04 for about 6 months sometimes installing Debian to check something, then installing Ubuntu again.  A few days ago I installed Debian.  Everything went fine.  I have to install the kernel from their Backports repository if that matters.  I then went to install Ubuntu 22.04.1 but I get this message on a blue screen.  "Verification failed:  (0x1A) Security Violation." 

So I select OK and I get another screen saying Press any key to perform MOK management.

I press a key and I get the first message again.  "Verification failed:  (0x1A) Security Violation."

Then I get a screen with the options Continue boot, Enroll key from disk, and Enroll hash from disk.

I I select Continue boot the first time I got a messagge from Support Assist (a dell application) saying something about restoring system to a working state.  I went ahead and did this but it didn't help.  On subsequent tries Support Assist stated to scan system but I pressed [ctr] [alt] [del] to start the boot process over.  Now it flashes a sign saying" failed to load image, start_image 0 returned security violation.  Then a screen comes on saying "no bootable device found" and restarts the boot process.

It was the same Ubuntu usb I've used before.  I tried putting the iso on a different usb but same result.  I put Ubuntu 22.10 on the first usb and it boots.  I then putn Ubuntu 22.04.1 back on the first usb and I get the same screens as above.

I tried restoring the BIOS to its original default settings but it didn't help.  I tried using a different usb port but it didn't help.

I've verified the iso.

The Ubuntu 22.04.1 usb does boot if I turn off Secure Boot.

I'm currently running Debian with the Gnome desktop.  Any help would be appreciated.

---

### Post by MAFoElffen on 2023-02-20
That the same 22.10 LTS USB worked previously, and now doesn't is perplexing. I think I would be confused also. I am certainly curious to what may be going on.

Just a sidenote: Is there a reason that you are needing 22.10 instead of an LTS Version like 22.04 LTS? (As being stable and long term support...)

I know a lot of people suggest turning off SecureBoot and the TPM,... But I have installed with both since 20.04 with no problems on my hardware... But 'some' hardware does not like those.

How was your 22.10 USB created from the ISO?

---

### Post by oldfred on 2023-02-20
What version of Ubuntu?
Is it only Intel video or do you have nVidia?

Since very new system, you need at least 22.04LTS. It is now at .1 and .2 with newer kernel will be out soon. You may need the .2 version.
Ubuntu 22.04.2 LTS Delayed To End Of February Over Kernel & Signed Shim Woes
[https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html](https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html)

My 11th Gen Intel chip based Dell 5310 installed without issues with Kubuntu 22.04. It only has Intel for video so no hassle on my assigning a MOK machine owner key for the binary blob that is the nVidia driver. if Secure Boot off, then you do not need MOK.
I even forgot to change UEFI settings from RAID and Secure Boot that I normally tell users they have to change and was required with old versions.
I did have to turn off Windows bitlocker & fast start up.

---

### Post by donald187 on 2023-02-20
> **MAFoElffen said:**
> That the same 22.10 LTS USB worked previously, and now doesn't is perplexing. I think I would be confused also. I am certainly curious to what may be going on.

Just a sidenote: Is there a reason that you are needing 22.10 instead of an LTS Version like 22.04 LTS? (As being stable and long term support...)

I know a lot of people suggest turning off SecureBoot and the TPM,... But I have installed with both since 20.04 with no problems on my hardware... But 'some' hardware does not like those.

How was your 22.10 USB created from the ISO?

Apologies.  My post was a bit involved and controverted.  It was the same 22.04 usb that worked previously and then didn't work.  As a test I temporarily put 22.10 on that same usb and it worked.  I then torrented a fresh copy of 22.04 and put it on that same usb and it still didn't work,  I also tried putting 22.04 on a different usb and it didn't work.

I use 22.04.  Not 22.10.

On Debian I use Gnome Disks to create the usb.  Specifically, I right click on the iso and select "Open with other application" and then select "Disk Image Writer".  Then select the usb drive.  But I believe it's all Gnome Disks.

I did recently do an update (one of those cumulative updates and one I don't remember) on Windows 11.  Perhaps something changed?

---

### Post by donald187 on 2023-02-20
> **oldfred said:**
> What version of Ubuntu?
Is it only Intel video or do you have nVidia?

22.04.  Only Intel video.

> 
Since very new system, you need at least 22.04LTS. It is now at .1 and .2 with newer kernel will be out soon. You may need the .2 version.
Ubuntu 22.04.2 LTS Delayed To End Of February Over Kernel & Signed Shim Woes
[https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html](https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html)


Just to be clear I've been on 22.04 for six months with Secure Boot enabled.  

I wondered if the .2 version would fix this.

---

### Post by oldfred on 2023-02-20
The link on 22.04.2 discusses some changes to shim, grub & kernel.
And getting the updates in sync, so an upgrade works for Secure Boot Not sure what they are changing.

I normally do not use Secure Boot on desktops, but I accidentally left it on for my Dell laptop & it worked. Have upgraded Windows & Linux still boots.
Have not tried reinstalling on laptop.

---

### Post by donald187 on 2023-02-20
> **oldfred said:**
> The link on 22.04.2 discusses some changes to shim, grub & kernel.
And getting the updates in sync, so an upgrade works for Secure Boot Not sure what they are changing.

Thanks.  I couldn't quite tell what they were saying.

---

### Post by donald187 on 2023-02-21
> **oldfred said:**
> The link on 22.04.2 discusses some changes to shim, grub & kernel.
And getting the updates in sync, so an upgrade works for Secure Boot Not sure what they are changing.

I normally do not use Secure Boot on desktops, but I accidentally left it on for my Dell laptop & it worked. Have upgraded Windows & Linux still boots.
Have not tried reinstalling on laptop.
Thanks. :)

---

### Post by donald187 on 2023-02-23
The 22.04.2 iso works! :)

---

