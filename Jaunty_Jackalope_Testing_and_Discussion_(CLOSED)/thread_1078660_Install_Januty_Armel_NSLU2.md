---
title: "Install Januty Armel NSLU2"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2009-02-23
Hi

I have been brave and reflashed my NSLU2 with the netboot insaller of Jaunty Armel version.

It flashes with no problems, when I go through and try and detect my usb drive I just get disconnected and have to restart again.

I have managed to install Debian 5.0 with no problems, but am having problems getting past the installer.

Anyone else have similar problems who have tried this?
How do i find what is actually causing the problem?

Thanks

Andy

---

### Post by andyrogers2008 on 2009-03-02
Hi Again

I have since gotten past my original problem but am now getting another problem which I have posted to the mailing lists here []("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-March/007284.html")

Or...

> Hi

Over the past few days I have been trying to install the latest Jaunty
build on my NSLU2, but seem to be having some problems.

I am using the latest di-nslu2.bin from
[http://ports.ubuntu.com/dists/jaunty/main/installer-armel/20081029ubuntu22/images/ixp4xx/netboot/](http://ports.ubuntu.com/dists/jaunty/main/installer-armel/20081029ubuntu22/images/ixp4xx/netboot/)
and it fixes all the previous problems of too much memory being used & the
locale language issue that has been also reported.

However now when Iam comming the end of the install, selecting the option
from the menu of "Finish Instillation", Iam getting asked a a little about
UTC time which I choose Yes to and then after a couple of minutes I loose
my SSH connection to my NSLU2.  I can relog back into it again but end
back at the installer menu on "Finish Instillation", but if I select this
again it just drops my SSH connection.

Has anyone been able to successfully install Januty on a NSLU2?
Am I doing anything wrong?

I have previously had Debian Lenny 5 installed with no problems during &
after instillation.  Iam mounting Januty to my USB Harddrive.

With the Debian 5 instillation, in the Instillation menu there is an
option of "Install Boot Loader" & "Countinue Without Bootloader".  In the
Jaunty installer there is only "Countinue Without Bootloader".
Is this correct or is their a menu option missing?

Thanks

Andrew

...

Can anyone point me in the correct direction for help with this during Januty testing, or even better help me here.

My original post seemed to fall on deaf ears.

My as I would love to get this going on my NSLU2 or otherwise I will be having to reinstall Debian 5 which I have no problems with at all.

Thanks

Andy

---

### Post by Th0mZ on 2009-03-08
Hi,

I've been trying to install jaunty on my nslu2 too.
I'm using a 8GB usb key.

I completed the installation, however at the end of the 'finish installation' option nothing happened. The progress bar disapears and it stays on an empty blue screen.

I also couldn't install a boot loader, only the 'continue without bootloader' option is available, with a message explaining how to boot manually:

"you will need to boot manually with the /vmlinuz kernel on partition /dev/sda1 and root=/dev/sda2 passed as a kernel argument"

I closed the SSH connection and re logged in a shell, mounted /dev/sda1 and runned /mnt/sda1/vmlinuz root=/dev/sda2

I get a permission denied error doing this...and i dont really know how this works so i'm not sure this will boot anyway...

About the loss of your SSH connection, i had this problem too, i had to reboot the nslu and restart installation. I think it's a problem of free memory on the nslu...on the second install i used the 'free memory' option after every step and didn't have the problem. Maybe this has nothing to do with it but you could try it.

Now I have no idea of how to boot jaunty. If you manage to get this thing working let me know, i'll keep trying too...

Sorry about my english, i'm french i'm doing my best...

Thanks,
Thom.

---

### Post by mfeif on 2009-03-09
Same problem here; the option to write the bootloader never showed.

I think I have a valid install, but can't boot to it.

I've tried various ways of flashing the NSLU2 with other firmwares, no-go.

Several threads on the net reference a tool called "flash-kernel" but I can't find this in either the installer filesystem or the installed "/target" filesystem.

Perhaps after going through install process again, and then dropping to a shell and apt-getting this tool?

---

### Post by ackbar345 on 2009-03-09
I've had similiar problems as the other posters here, the message about no bootloader being installed. I had Debian up and running on an 8gb flash drive but after awhile it crashed and burned. I decided it was time to move to a USBHDD and Ubuntu has become my preferred linux distro.

I also can't log on as the user I set up, presumably because there is no bootloader. I am going to put Debian back on the box because I need it up and running ASAP.

---

