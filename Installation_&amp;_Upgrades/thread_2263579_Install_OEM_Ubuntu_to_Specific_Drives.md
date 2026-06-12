---
title: "Install OEM Ubuntu to Specific Drives"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by Jack_Lam on 2015-02-01
Hi all,
    Apologize if I ask silly questions, I try to make a customize Ubuntu system to my client (with the default environment set), I follow the below procedures and successfully made a OEM USB ready for the customer

1) Download the Ubuntu ISO and make a bootable USB

2) Boot up the USB and get into the OEM shipment env, do all the env setup following the below guide
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

3) Everything went fine, and I click the prepare for shipment button, shutdown my machine.

4) I then pass the USB to the client to let him install the Ubuntu together with the custom env

My problem is
1) When the client install the Ubuntu, it directly install to the USB instead of his hard drive, the client wants to install the OEM ubuntu to its hard drive, how can I achieve this?

2) Also, when before the client installed the OEM ubuntu, they can make user themselves, and that user is in the sudo group which in turn letting him to be root after installation, can I forbid this action, i.e. whatever user account he/she made cannot turn into sudo group?

Thanks and appreciate all for the help

---

### Post by grahammechanical on 2015-02-01
Did you test this USB OEM installer before giving it to the client? Is the client using the Try Ubuntu session and not the Install Ubuntu session? Is the client following these instructions?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

What option is the client selecting out of

Install Ubuntu alongside
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

Please explain the actions this client carried out. I do not think that it is possible to run Ubuntu from a USB memory stick and then install Ubuntu onto the same USB memory stick. And yet that seems to me to be what you are saying this client is doing.

As far as I understand things every installation of Ubuntu needs at least one user with administrator privileges. What will happen if there is a security update to the Linux kernel that requires authentication and there is not one user on the system that can authenticate that action? Do you not agree that your clients need the freedom to administer their own computers? You cannot do it because you are not set up as a user on that installation.

> [COLOR=#333333][FONT=Ubuntu]Now choose a password for the temporary [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]oem[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] user which will have full administrative powers. Make sure to remember it.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Now you can install addition software, drivers or configure the system as desired. When you're done doing that click on the [/FONT][/COLOR]**Prepare for shipping to end user**[COLOR=#333333][FONT=Ubuntu] icon on the desktop.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]This removes the [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]oem[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] user on next boot.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Once the computer was shipped to the end user and he finally boots for the first time he will be taken to the system setup wizard where he will be able to set his location, keyboard layout, user name etc.[/FONT][/COLOR]

Regards.

---

### Post by Jack_Lam on 2015-02-02
> **grahammechanical said:**
> Did you test this USB OEM installer before giving it to the client? Is the client using the Try Ubuntu session and not the Install Ubuntu session? Is the client following these instructions?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

What option is the client selecting out of

Install Ubuntu alongside
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

Please explain the actions this client carried out. I do not think that it is possible to run Ubuntu from a USB memory stick and then install Ubuntu onto the same USB memory stick. And yet that seems to me to be what you are saying this client is doing.

As far as I understand things every installation of Ubuntu needs at least one user with administrator privileges. What will happen if there is a security update to the Linux kernel that requires authentication and there is not one user on the system that can authenticate that action? Do you not agree that your clients need the freedom to administer their own computers? You cannot do it because you are not set up as a user on that installation.









Regards.

Thanks for the quick reply!

Is the client using the Try Ubuntu session and not the Install Ubuntu session? >>* he didn't even being asked for try or install Ubuntu, just straight forward to ask username, keyboard layout and directly into the login page.*

Actually, the client said first he is asked to select the language
[IMG]http://s29.postimg.org/69u3h82lh/image.jpg[/IMG]

Then straightly being asked for location
[IMG]http://s29.postimg.org/cot4dw9b9/image.jpg[/IMG]

Now you can install addition software, drivers or configure the system as desired. **When you're done doing that click on the Prepare for shipping to end user icon** on the desktop.>>*I have clicked the prepare shipping to end user and after that I **shutdown the machine** and **pass the USB to my client***


Once the computer was shipped to the end user and he finally boots for the first time he will be taken to the system setup wizard where **he will be able to set his location, keyboard layout, user name etc.**>>*Exactly, but he is not able to choose where to install, the wizard just ask for creating user account, keyboard layout etc. But without asking him to choose any partitions to install. I wonder if the user needs to do anything special to trigger it?*

I do not think that it is possible to run Ubuntu from a USB memory stick and then install Ubuntu onto the same USB memory stick>>[I]Exactly, that is what I think is quite strange, but finally, the installed Ubuntu is actually located in the USB, quite weird. During the processes, Ubuntu does not ask for the installation partition.
[/I]
Do you not agree that your clients need the freedom to administer their own computers?[I] >> I don't want the client to touch too many things, afterall his computer just sit on a LAN without reaching to the Internet, therefore system update is not important to him
[/I]
You cannot do it because you are not set up as a user on that installation.[I]>> Then can I use any workaround which skip asking the username and password (with some modification on the OEM install with pre-set username and password)??

[/I]Thanks!

---

### Post by lisati on 2015-02-02
I might be mistaken for recent releases, but the last time I checked out the OEM setup (it was a few years ago), it assumed that you were going to run Ubuntu from the device it was installed to.

---

### Post by Jack_Lam on 2015-02-02
> **lisati said:**
> I might be mistaken for recent releases, but the last time I checked out the OEM setup (it was a few years ago), it assumed that you were going to run Ubuntu from the device it was installed to.
Oh, that's not want I want, can I modify the OEM installation process to let it add back the wizard of selecting the installation partition?

---

