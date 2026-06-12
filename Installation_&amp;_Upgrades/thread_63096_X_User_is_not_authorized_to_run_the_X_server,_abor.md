---
title: "X: User is not authorized to run the X server, aborting."
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by drunktiger21 on 2005-09-06
Hi, I am new to the forums.

 I have just recieved Ubuntu and this is my first time using Linux. It is much more different than i expected from windows.

Here is my issue, I have done a fresh install of Ubuntu. And I've done researching on how to install files. And a few sources told me to use the "X"/"xstart"/"startx" command, whenever I do, I get the following message:

X: User is not authorized to run the X server, aborting.

I have no idea what am i doing wrong or what, but it will not let me go into the x server.

I have checked and "allow-user-xsession" is enabled.

Thanks for any help,
Drunktiger21

---

### Post by amohanty on 2005-09-07
Drop into recovery mode. On the command prompt type:

cd /home/<username>
where username is the login of the first user.

then post the output of
ls -l .Xauthority .ICEauthority

If it does not say somthing like:
-rw-------  1 <username> <username> 2153 2005-09-06 20:57 .ICEauthority
-rw-------  1 <username> <username>  171 2005-09-06 20:57 .Xauthority

Then do the following at the prompt:

chown <username>:<username> .Xauthority .ICEauthority

REMEMBER replace <username> with the login of the first user.

HTH
AM

---

### Post by drunktiger21 on 2005-09-07
-rw-------  1   boris boris 161 2005-09-07 10:03 .ICEauthority
-rw-------  1   root root 118 2005-09-06 13:08 .Xauthority

Thanks in advance

---

### Post by amohanty on 2005-09-07
> -rw------- 1 root root 118 2005-09-06 13:08 .Xauthority 

this is the black sheep here. you would want it to look like:

> -rw------- 1 boris boris 118 2005-09-06 13:08 .Xauthority 

To do so, in the GRUB menu select the recovery mode option. It will take you to a command prompt.

there type the following:

cd /home/boris
chown boris:boris .Xauthority
shutdown -r now

the last one just reboots the machine.

HTH
AM

---

### Post by drunktiger21 on 2005-09-07
When I entered 

chown boris:boris .Xauthority .ICEauthority

in the recovery mode option (failsafe terminal for me), it says changing .Xauthority. Operation not permitted.

And when I enter

shutdown -r now

The console tells me that I need to be root to do that.

---

### Post by amohanty on 2005-09-07
whoops forgot the sudo.. sorry about that. Try this:

sudo chown boris:boris .Xauthority .ICEauthority

It will prompt for the password, enter your own password.

HTH
AM

---

### Post by drunktiger21 on 2005-09-08
Now, I have no idea what works what doesn't since I have tried so many different commands.

I guess where I was going with this whole thread is I am trying to install Ndiswrapper from [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) to install a windows network adapter driver. And then I need help installing an intel graphics driver located at [http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://aiedownload.intel.com/df-support/8203/eng/i915Graphics.tar.gz&agr=&ProductID=865&DwnldId=8203&strOSs=&OSFullName=&lang=eng](http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://aiedownload.intel.com/df-support/8203/eng/i915Graphics.tar.gz&agr=&ProductID=865&DwnldId=8203&strOSs=&OSFullName=&lang=eng)

Thanks.

PS-  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

EDIT- do you have AIM by any chance?

---

### Post by amohanty on 2005-09-08
I think there are tons of posts with details regarding installing ndiswrapper. Just do a search and you will find it.

AM

---

