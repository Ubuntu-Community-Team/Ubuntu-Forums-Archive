---
title: "Clarifying download/install process, verifying download and WSL"
date: 2022-12-04
forum: Installation &amp; Upgrades
---

### Post by mollie4168 on 2022-12-04
Hello,

I have gone down multiple different rabbit holes and I'm now just generally confused.  For context, I've been using Ubuntu for 15 years, but my knowledge is pretty basic, so talk to me like a noob.  My 9 year old laptop just died (so I haven't done much of this in a long time), and I have a new Dell Windows 11 laptop.  End goal is to nuke Windows and return to Ubuntu.

First problem: my Ubuntu stick didn't turn out right (it got stuck on the start up Dell/Ubuntu screen when trying to test/install Ubuntu), so I began investigating that.   I'm hoping the end of this problem is that I'm picking up a brand new USB later to start completely over.  

When I looked a week ago, the download instructions had me use Rufus and now it says to use balena etcher.  I've attempted to re-do the bootable USB a few times, and it says that it completes, but checking the diskpart, the USB doesn't look like it's set up right. Also, while it's writing the ISO, Windows is telling me the disk needs to be formatted, but it's write-protected.  I've been through instructions for formatting a write-protected disk a few times.  Again, hoping this will resolve with completely starting over with a brand new USB.  

I started trying to verify the download using these instructions ([How to verify your Ubuntu download | Ubuntu]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#4-retrieve-the-correct-signature-key")), but I keep getting 
[HTML]gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMSgpg: can't open 'SHA256SUMS.gpg': No such file or directorygpg: verify signatures failed: No such file or directory

gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com --recv-keys 0x46181433FBB75451 0xD94AA3F0EFE21092gpg: key D94AA3F0EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changedgpg: key 46181433FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changedgpg: Total number processed: 2gpg:              unchanged: 2
[/HTML]

What am I missing here?

Through the course of this process, I discovered and downloaded WSL.  To verify, should I be able to follow all the instructions for Ubuntu (as opposed to Windows) if I am using WSL?  Can I do everything I can do in Ubuntu through the WSL terminal?

(Also, I'm assuming the answer is no, but can I download the full Ubuntu--more than the app--to do a full system test and installation through WSL?)

Ultimate questions:
What are the tasks I actually need to do besides successfully make my bootable USB?   
Do I need WSL and the Ubuntu app?  If so, please clarify how much I should be able to accomplish through WSL when using Ubuntu-focused instructions on a Windows device.  
Also, any thoughts on why it's not importing the SHA256SUMs files?  I've downloaded them.  I've gone through the Verify the download instructions from the link above through step 4 and tried to start Step 5.

Thank you.

---

### Post by grahammechanical on 2022-12-04
You are asking two serious questions in the same post. Trying to answer two questions in the same thread will produce a very confusing discussion. Please select one of these two questions to be answered in this thread and then ask the other question in a separate post/thread.

> but checking the diskpart, the USB doesn't look like it's set up right.

This is what the balenaEtcher instructions have to say under Frequently Asked Questions

> How do I flash Ubuntu ISOs

Ubuntu  images (and potentially some other related GNU/Linux distributions)  have a peculiar format that allows the image to boot without any further  modification from both CDs and USB drives.
A consequence of this enhancement is that some programs, like parted get  confused about the drive's format and partition table, printing  warnings such as:
/dev/xxx contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it  should. Perhaps it was corrupted -- possibly by a program that doesn't  understand GPT partition tables. Or perhaps you deleted the GPT table,  and are now using an msdos partition table. Is this a GPT partition  table? Both the primary and backup GPT tables are corrupt. Try making a  fresh table, and using Parted's rescue feature to recover partitions.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
All these warnings are safe to ignore, and your drive should be able to boot without any problems.
Refer to [the following message from Ubuntu's mailing list]("https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html?d_id=10fdd908-859d-4d61-bd7a-5c0d9b1bac1e&s_id=1670169378052") if you want to learn more.

I seriously doubt if a Windows partition manager has the ability to understand Linux ISO images and the partitions of an ISO image flashed to a USB memory stick.

[https://www.balena.io/etcher/](https://www.balena.io/etcher/)

Regards

---

### Post by SeijiSensei on 2022-12-04
If you have access to an Ubuntu machine, you'd be better off creating the USB there. 

I have used Rufus, and I worked fine for me.

Any reason not to install VirtualBox on Windows and create an Ubuntu virtual machine? You don't need to make a USB if you go this route. You can just install from the downloaded ISO image.

---

### Post by ubfan1 on 2022-12-04
To validate, you should hashcheck the downloaded iso (sha256sum ...iso) compare the result with the published result from the Canonical site, regardless of where you downloaded the iso.
Then, to ensure the published result is from Canonical, you can check its signature, or not -- up to you how paranoid you feel about your download.

---

### Post by mollie4168 on 2022-12-05
No longer have an Ubuntu machine.  

I don't think I want to do an Ubuntu virtual machine because I just really hate Windows.  But I'll look into a virtual box.  This is the first I've heard of it.  

Thank you!!

---

### Post by mollie4168 on 2022-12-05
What does it mean to hashcheck?  Thank you!

---

### Post by mollie4168 on 2022-12-05
Thank you for the information!  I will look into it further when I try the bootable USB again.  It's going to take me a few days to get back to this again, but I'll start with the USB and verifying the download.

---

### Post by tea for one on 2022-12-05
> **mollie4168 said:**
> What does it mean to hashcheck?  Thank you!
Imagine that you have downloaded [COLOR="#0000FF"]ubuntu-22.10-desktop-amd64.iso[/COLOR] and it is located in your Downloads folder.
Open a terminal and enter:-
```
cd Downloads
```
```
sha256sum ubuntu-22.10-desktop-amd64.iso
```
Result is
```
sha256sum ubuntu-22.10-desktop-amd64.iso 
b98f13cd86839e70cb7757d46840230496b3febea309dd73bd5f81383474e47b  ubuntu-22.10-desktop-amd64.iso
```
Then, you compare this huge line of text with the published sha256sum of the ISO [https://releases.ubuntu.com/kinetic/](https://releases.ubuntu.com/kinetic/) > SHA256SUMS

I usually open a text editor and copy /paste the the published hash on the first line and the terminal output on the second line:-
```
b98f13cd86839e70cb7757d46840230496b3febea309dd73bd5f81383474e47b *ubuntu-22.10-desktop-amd64.iso [COLOR="#0000FF"]Published Hash - note asterisk[/COLOR]
b98f13cd86839e70cb7757d46840230496b3febea309dd73bd5f81383474e47b  ubuntu-22.10-desktop-amd64.iso [COLOR="#0000FF"]Terminal output[/COLOR]
```
The sha256sums are identical and the downloaded iso is verified.
If the sha256sums are different, then the download is damaged and potentially compromised.

---

### Post by ne29914 on 2022-12-05
> **mollie4168 said:**
> Hello,
Also, while it's writing the ISO, Windows is telling me the disk needs to be formatted, but it's write-protected.  I've been through instructions for formatting a write-protected disk a few times.  Again, hoping this will resolve with completely starting over with a brand new USB.  
.
This stood out. Are you certain that there isn't a little mechanical switch on the thumb drive that write-protects it?
Just an idea,.

---

### Post by mollie4168 on 2022-12-10
Thank you everybody for your assistance.  The original sha256sum directions seemed to overcomplicate things, but I ended up doing essentially what teaforone was suggesting, and it worked out fine. One of the challenges was figuring out the file path on a Windows filesystem, but I eventually got there.  Ubuntu installed.

Ne29914, no switch on the thumb drive.

Thanks all!

---

