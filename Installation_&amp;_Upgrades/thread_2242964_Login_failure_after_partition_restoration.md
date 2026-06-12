---
title: "Login failure after partition restoration"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2014-09-05
Hello,

I am running Ubuntu 12.04 LTS with GNOME Shell 3.4.1 in Classic mode, in double boot with Windows XP. In trying to resize my Ubuntu home partition with GParted I accidently messed up my data although the partition remained intact. I thus decided to restore the partition with a back-up of the home folder which I had made by copying to an NTFS external disk.

I used a live CD to copy in the back-up home folder with rsync, then fixed the mount parameters in fstab. Now GRUB2 works fine on boot, and I can boot into Windows. But when I try to boot into Ubuntu, the login-dialogue first accepts my password, then returns to the dialogue box to ask again for a password (when I give an incorrect password, it is rejected, so I assume that my password is recognised).

I have seen in previous posts (see [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)) that similar problems can be caused by .Xauthority file. I could not find .Xauthority in my installation, nor strangely in my back-up, and it is not generated when I try to log into Ubuntu. I copied in the .Xauthority file from another computer running with the same Ubuntu version and the same password, but the situation did not change, I still get a password loop.

Your advice on how to reactivate Ubuntu login would be greatly appreciated.

Thanks and best regards, John

---

### Post by John_Rose on 2014-09-05
Hello again, I think I see the problem but I am a baby at this and need someone to guide me through.

When I check my home directory from the live CD I see that the group and user are both "ubuntu". When I boot directly and load a tty (I cannot login graphically) I cannot access the home directory since it says I don't have the permissions. It seems that when I backed up my home directory into an NTFS I lost the user information so that bringing it back in (even with rsync) resulted in home folder files without the right user and group (which should be "john:john").

But when I checked on a working Ubuntu system using a live CD, I found that the user and group for files in the home directory were "1000:1000" and not "john:john", even though they are "john:john" when I boot normally into Ubuntu. I assume that if I could change the ownership of my home directory content (equivalent to "sudo chown -R user:user /home/user") then my Ubuntu might work, but what is the right method (can I say from  a tty in the live CD something like "sudo chown -R john:john UUID" or "sudo chown -R 1000:1000 UUID" where UUID is that of my home directory partition?)?

Hoping that someone will take pity and reply soon, thanks and best regards, John

---

### Post by Bashing-om on 2014-09-05
John_Rose; Hang'n with you,

I think you have the guist of it right, Change the /home directory back to "you".
Make sure the file " .ICEauthority " also exist in your /home directory.
Easier less complicated if we can do this from the install. What results when at the log in screen you do:
ctl+alt+F1 ??
Can you log in here ?

Else yeah, will set up a full CHange Root in the liveDVD and change those access rights.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by John_Rose on 2014-09-06
Thanks for your support Bashing-om.

When I booted in from GRUB2 to ubuntu it said:

[B]No directory, logging in with HOME=/
To run a command as administrator (user "root"), use "sudo <command>".[/B]

With alt+ctl+F1 (or with F2 to F6) I could login with my user name "john" and my password. But I could not access /home (which had ubuntu:ubuntu as the user) even with sudo.

So I rebooted from the live CD and used the terminal alt+ctl+T (same user "ubuntu" as with alt+ctl+Fx but it works with the French keyboard - alt+ctl+Fx expect an English keyboard and impossible to get the console-data package to change it), and did the following:

1) added the user "john":

[B]ubuntu@ubuntu:/$ sudo adduser john
Adding user `john' ...
Adding new group `john' (1000) ...
Adding new user `john' (1000) with group `john' ...
Creating home directory `/home/john' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for john
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y
ubuntu@ubuntu:/$[/B]

2) changed the owner of the "john" directory in /dev/sda5 (home for the directly booted system) to "john:john":

[B]ubuntu@ubuntu:/$ sudo chown -R john:john /media/c1443e7a-eef9-4374-9c08-c14c1fb98387/john
ubuntu@ubuntu:/$[/B]

3) changed the owner of "Lost+Found" to "root:root":

[B]ubuntu@ubuntu:/media$ sudo chown -R root:root c1443e7a-eef9-4374-9c08-c14c1fb98387/lost+found
ubuntu@ubuntu:/media$[/B]

Now I could not longer access sda5 from the graphical interface or from the terminal (because was logged in as "ubuntu"). I rebooted directly from GRUB2 and got the same login loopback. Then I entered the alt+ctl+F1 terminal (which works directly with the French keyboard) getting the same message as before:

[B]No directory, logging in with HOME=/
To run a command as administrator (user "root"), use "sudo <command>".[/B]

But I could confirm that the users for home directory are now OK: "root:root" for "/home" and "/home/Lost+Found" and "john:john" for the directory "home/john".

So it still does not work even though the home directory should be OK, where to go from here?

Best regards, John

---

### Post by John_Rose on 2014-09-06
Hello again,

I looked more carefully and found that the permissions for the /home directory:

[B]john@JOHN-PC:/$ sudo ls -la home
total 28
drwxr-----  4  999  999  4096 déc.  29  2010 .
drwxr-xr-x 23 root root  4096 juil. 21 16:19 ..
drwx------ 64 john john  4096 sept.  6 10:11 john
drwx------  2 root root 16384 déc.  29  2010 lost+fou[/B]nd

were not quite the same as those on my companion netbook with the same Ubuntu configuration:

[B]drwxr-xr-x  4 root root  4096 déc.  29  2010 .
drwxr-xr-x 23 root root  4096 juil. 21 16:19 ..
drwxr-xr-x 64 john john  4096 sept.  6 10:11 john
drwx------  2 root root 16384 déc.  29  2010 lost+found[/B]

When I changed them, Ubuntu booted fine. So let's count this as solved, thanks, I will be updating the configuration and will come if other problems.

Best regards, John

---

### Post by Bashing-om on 2014-09-06
John_Rose; Great !

You do good work . We will await and see if there are an further developments. I expect all is now in good order.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

