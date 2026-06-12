---
title: "Installing Ubuntu Dual boot On A Acer all in one Desktop"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-07-25
Hello everyone I have a question about install Ubuntu on a Acer machine. I have a Acer all in one desktop and I wanted to Install Ubuntu on it but from what I've been reading there's a few things I need to do to get around UEFI

I know I have to disable Secure boot, Enable Boot menu, not sure what else I'm missing

This machine has Windows 10, so I don't want to mess anything up. I want to make sure I install the boot loader in the correct order so I have the choice to choose what operating system I want to boot

I have all Dells this is my first Acer and they have made it a bit harder to load Linux on it that's why I asking what would be the safest way to approach this task

I didn't list the specs because it's a new machine and I'm sure Ubuntu will run on it without a doubt 

I found a thread from Oldfred that explains a few things needed to get things working
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)


Thanks so much everyone

---

### Post by yancek on 2016-07-25
Did you read the Ubuntu documentation on dual booting with windows uefi?  If windows 10 was pre-installed, it is almost certainly using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by RobGoss on 2016-07-25
Yea I have and I also have machines dual booting, but from what I understand it's  a bit different using a Acer machine

 Thanks anyway

---

### Post by QDR06VV9 on 2016-07-25
Sorry I am not of more use here...but if you do not want to mess-up Windows 10 Drive, maybe consider another hard drive to play on.
New Acer's and Lenovo's can be a bit tricky..and procedures vary from machine to machine.
I have A couple of friends that do that and they are not very tech savy....with this method they do not seem t call me much for Install Questions.
Just a thought...Kind Regards

---

### Post by oldfred on 2016-07-25
While I like to have an operating system on every drive and have installed Ubuntu to both sdb & full install to a larger flash drive, the procedure to install to an external drive with UEFI is a bit more complex. You have to gpt partition in advance, use Something Else to choose install partition(s) on external. And no matter what you say about installing grub to any place other than the ESP - efi system partition on sda, it only installs to sda's ESP. It overwrites my main install's /EFI/ubuntu and I have to copy that to the external drive and restore my backup of my ESP's /EFI/ubuntu.

Oldfred also has some summary UEFI install instructions in link below. Yancek's link is the most important.
But backup of Windows and using Windows to shrink its own NTFS partition is preferred.

---

### Post by RobGoss on 2016-07-25
> **runrickus said:**
> Sorry I am not of more use here...but if you do not want to mess-up Windows 10 Drive, maybe consider another hard drive to play on.
New Acer's and Lenovo's can be a bit tricky..and procedures vary from machine to machine.
I have A couple of friends that do that and they are not very tech savy....with this method they do not seem t call me much for Install Questions.
Just a thought...Kind Regards

Thanks for the advice much appreciated 

I'm not to worried about messing things up I just wanted to make sure when I install Ubuntu it boots correctly and gives me the option to choose which operating system I want

I was reading on Acers you need to setup a password for UEFI to trust Ubuntu in order to get it installed

I have machines with UEFI and I never had to do this before so I wanted to clarify it

---

### Post by RobGoss on 2016-07-25
> **oldfred said:**
> While I like to have an operating system on every drive and have installed Ubuntu to both sdb & full install to a larger flash drive, the procedure to install to an external drive with UEFI is a bit more complex. You have to gpt partition in advance, use Something Else to choose install partition(s) on external. And no matter what you say about installing grub to any place other than the ESP - efi system partition on sda, it only installs to sda's ESP. It overwrites my main install's /EFI/ubuntu and I have to copy that to the external drive and restore my backup of my ESP's /EFI/ubuntu.

Oldfred also has some summary UEFI install instructions in link below. Yancek's link is the most important.
But backup of Windows and using Windows to shrink its own NTFS partition is preferred.

Hi Fred, I should have added dual booting in my title
I want to dual boot this machine with Windows 10 and Ubuntu. But I understand there are a few things I need to change in the bios. Like setting a password to allow UEFI to except Ubuntu installation is that correct?

---

### Post by RobGoss on 2016-07-25
> **oldfred said:**
> While I like to have an operating system on every drive and have installed Ubuntu to both sdb & full install to a larger flash drive, the procedure to install to an external drive with UEFI is a bit more complex. You have to gpt partition in advance, use Something Else to choose install partition(s) on external. And no matter what you say about installing grub to any place other than the ESP - efi system partition on sda, it only installs to sda's ESP. It overwrites my main install's /EFI/ubuntu and I have to copy that to the external drive and restore my backup of my ESP's /EFI/ubuntu.

Oldfred also has some summary UEFI install instructions in link below. Yancek's link is the most important.
But backup of Windows and using Windows to shrink its own NTFS partition is preferred.

Hi Fred, I should have added dual booting in my title
I want to dual boot this machine with Windows 10 and Ubuntu. But I understand there are a few things I need to change in the bios

Like setting a password to allow UEFI to except Ubuntu installation is that correct?

Just to clarify this is not a external hard but on board one in this Acer desktop


From what I understand this is needed for Acer machines

---

### Post by oldfred on 2016-07-25
Acer seems to be the only one that has the requirement of setting a supervisory password and then enabling trust on the .efi grub boot files in the ESP. Some older threads may mention downgrading UEFI, but at least one newer one says latest UEFI from Acer works, so best to make sure you have newest UEFI from Acer even if a new system. And some have needed boot parameters.

You found at least on thread where users with Acer posted what they had to do. Some are a bit clearer than others. I do not have Acer, so have not had to do any of that. My UEFI systems are all Desktops which seem to have more UEFI capabilities (but more settings to sort thru).

(trying to post a bunch of links to other Acer threads, but forum then says I do not have permission). Ongoing issues with forum.
You should be able to search forum for oldfred & Acer (I use google and site:ubuntuforums.org as part of search).

---

### Post by RobGoss on 2016-07-25
Thanks Fred for the tips I found a few threads of your on this topic and will continue to search

Have a great day and thanks for your time

---

### Post by RobGoss on 2016-07-25
Thanks Fred for the tips I found a few threads of your on this topic and will continue to search

Have a great day and thanks for your time

---

