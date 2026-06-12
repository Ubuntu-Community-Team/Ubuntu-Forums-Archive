---
title: "Direct support for Ubuntu Budgie?"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by xcfstarflight1 on 2020-04-09
Hi!
I have been using Ubuntu on and off alot but my install is so messed up I am doing a clean one now and this time with Budgie.
I read about Budgie and it sounded quite like the same old Ubuntu but with some additional pampering of the GUI.

I will be doing the install today and try it out. Hopefully this will be a convenient flavour for me and hopefully i will like it.

The reason for posting this thread however is to hear if this  forum will help out with Budgie questions or discussions spesificaly?
And also to hear if anyone else using the flavour who can give me some first time user help and just basically get started in a good way :)

Ubuntu is my linux distro of choice just because of loyality and because I like it. Also, the people on the ubuntuforums are so kind and 
helpfull. 

I will be doing a clean install now in about an hour or so. If anyone have time, read the footnote of this thread. 

Love y'all 

By the way, *i would have love to have someone to chat with. I have a discord server, you can locate me there, I use IRC from time to time. *

---

### Post by deadflowr on 2020-04-09
> The reason for posting this thread however is to hear if this forum will help out with Budgie questions or discussions spesificaly?
Yes.
Ubuntu Budgie is an official Ubuntu flavor.
All Ubuntu Flavors get equal treatment here.

---

### Post by xcfstarflight1 on 2020-04-09
Allright. I will go ahead and install the Budgie to a CD-ROM and start exploring :-) 
Thanks for your kind respond. 

Just another thing, if anyone reads this thread.. I am looking for Ubuntu official documentation (tutorials and general) in video format, since I am such a slow reader :-O

---

### Post by DuckHook on 2020-04-09
> **xcfstarflight1 said:**
> …my install is so messed up I am doing a clean one now and this time with Budgie…
Budgie is an excellent flavour (they all are). To not have to do this again, try to keep your base install as close to default as possible. That means don't add PPAs or many apps or customizations to your base install. The closer it is to its pristine state the less issues you will have. If you want to experiment with the OS, do so in a VM. If you want to add tons of apps, do these in VMs too (if possible), or, if you are feeling adventurous, try the new-ish method in the link in my sig: *Sandboxing apps with LXD*. A word of caution: at this point, this method is still quite technical with few users, so it should be considered experimental/unstable.

---

### Post by DuckHook on 2020-04-09
> **xcfstarflight1 said:**
> …I am looking for Ubuntu official documentation (tutorials and general) in video format…
Not strictly Ubuntu, but one of the best visual ***Linux*** intros is: [https://linuxjourney.com](https://linuxjourney.com)

---

### Post by Frogs Hair on 2020-04-09
Ubuntu Budgie has a support site for desktop specific questions that is linked in the applications menu. 
 [https://discourse.ubuntubudgie.org/](https://discourse.ubuntubudgie.org/)

---

### Post by xcfstarflight1 on 2020-04-09
Well.. I will have one administrator doing all the installation of what I need.
I will have one main user for my work.
I will also be having a user for media, I will have some applications installed for recording audio and photography etc. that this user will have.
But I really need to know one thing and really do it correctly this time. 
I need a shared folder between the two users that are not administrator! 
Must the users be in the same group or is this default if so how to just make a shared folder for my files??

---

### Post by xcfstarflight1 on 2020-04-09
Is anyone still following my thread? I got asked to install Ubuntu with the ZFS filesystem. Now, I did not do this because it is experimental and as people on the thread wrote,
I should not be doing too much of that :) 
Other thing is the encryption. I didn't do that either.
Thou I wonder, I might need to disable secureboot. But what is the Unlock bootloader? Something in Linux or something in BIOS?
Feeling really exited now as the installation is complete! :) Yayy!

---

### Post by xcfstarflight1 on 2020-04-09
I am in love <3

---

### Post by DuckHook on 2020-04-09
It seems to me that you are breaking up your users a bit much. Do you really need to switch users for these tasks?

In Windows, one is often advised to switch from admin to a different user for everyday computing. That's necessary in Windows because of Windows' peculiar limitations. But in Ubuntu, the admin account is not activated. The use of sudo just elevates you to admin level for a brief time and only so long as the command is prepended by sudo. Otherwise, you are already just a typical user.

Also, why a different user for media? Is this an account that others will be accessing and you don't want them to access your regular work? If you are the only user on the computer, then, again, splitting off another user may be overkill. It adds to complexity without gaining you any real advantage.

The reason for creating another user should be because s/he is truly a physically distinct user. If you are the only one on the computer, then avoid unnecessary complexity. This may be the reason that it caused you previous problems and necessitated the re-install. If you are worried about rogue apps, then sandbox them using any of the methods that already exist: VMs, Firejail, Apparmor, or the experimental one I recently added to my sig.

If there are truly separate users on one computer and you want to share files between two users, there are as many ways to do so as there are opinions on the subject. Here is my suggestion based on the least possibility for grief.

[LIST=1]
[*]Do not allow promiscuous access to any of the real users' $HOME directories. This way, you won't risk gumming them up.
[*]Create a new user for the sole purpose of sharing its directory. This new user is a "dummy" user, but its directory will be useful:```
sudo useradd -d /home/shared -m shared
```
[*]Set "shared"'s password. Make it the same as the one used for your account (to make administration easier):```
sudo passwd shared
```
[*]Set new directory's permissions to sane values and limit access for security purposes:```
sudo chmod 770 /home/shared
```
[*]For every user who requires shared access, add them to "shared"'s group:```
sudo usermod -a -G shared xcfstarflight1
sudo usermod -a -G shared xcfstarflight2
sudo usermod -a -G shared xcfstarflight3
…
```
[/LIST]
These users should now be able to access /home/shared, add, read and delete files, etc *if the constituent files have the proper permissions*. Note, however, that when first starting out, Linux permissions and ownership can be very confusing. If User1 creates a file, then even though it is stored in /home/shared, this does not mean that User2 can read it. User1 is still the owner of the file, and if the file permissions have been set to something like 550, then User2 cannot read this file. If you want to share files in the Linux-sphere, you must understand the underlying concepts of ownership and permissions.

For a good primer on Ownership and Permissions:
[https://linuxhandbook.com/linux-file-permissions/](https://linuxhandbook.com/linux-file-permissions/)

---

### Post by xcfstarflight1 on 2020-04-09
Thank you so much. You are right, I don't need more users for the purposes I mentioned.
I have a small one man business and I just hired one person who should have a user on my computer.
It will just be my used (that is admin) and him. But i do not want him admin rights but just access to t hat share.

Thanks I hope I do not mess this up again :)

---

### Post by DuckHook on 2020-04-09
So you need just one additional user. Therefore, the last part of my previous post is overkill. Your situation is much simpler:

[LIST=1]
[*]Create a new user for your new hire. Everything s/he produces goes straight into his/her default directory.
[*]Using the one-line instruction in my prior post, grant yourself access to his/her directory by making yourself part of his/her group.
[*]Presto: you have access to your new hire's directory, but s/he has no access to yours.
[*]Shared files simply get deposited in his/her directory, not yours. Remember to set permissions for these files so that s/he can access them.
[/LIST]
It's that simple.

---

