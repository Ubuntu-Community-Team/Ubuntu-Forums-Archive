---
title: "retrieve password?"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by brainstuff on 2005-02-25
Hi folks
I burnt a friend of mine the Ubuntu CD for him to install, which he did  last night. Between the hours of 12-4am. 

Needless to say he wasn't exactly * compus mentis* at the time, and now he doesn't remember ever entering a password during setup, let alone what it was. This is user password NOT root.

Is his only recourse to re-install from scratch or is there any way he can reset something to get back in?

By the way, I am not talking about myself in the third person to save embarrassment, this is actually true  :p

---

### Post by bored2k on 2005-02-25
ubuntu/knopp!x live disc is ur friend ...

"You basically have to gain access to your machine somehow to alter the respective files. A pretty convenient way is to use the bootable installation CDs of some Linux distro and launch some "recovery console". If you can't see some comand like that you might try the ALT+F1..Fx keystroke to maybe get a clear console.

Once you have managed to get into a shell you need to mount the partition that holds your /etc directory. To reset the root password open the file /etc/passwd and look for a line starting with ...

root:x:.........

Delete the "x" in this line as it tells that the password is shadowed. Save the file.

Secondly open /etc/shadow and search for the entry for the user "root". This one usually looks like this ...

root:$s0m3fR1g9InMD5h45H:<numbers>:<more numbers>::::

Delete all values (the stuff between the columns) so that you get a line like this ...

root::::::::

Save the file, unmount the partitions and reboot. The root-account should not have set a password now, which you should change immediately again.

hope that helps"  taken off the net

---

### Post by thestarman on 2005-02-25
[QUOTE=brainstuff]... now he doesn't remember ever entering a password during setup, let alone what it was. This is user password NOT root.[/QUOTE]

Does he know the root password, then?  If so, he can change the passwords of any user!  If not, then just boot up the system into a low enough run level and change the root password to one he will remember! When you first boot up, with either GRUB or LILO, get into 'edit mode' and add the word "single" to list of options. After that boot up system.  You should now be able to simply ENTER the command: **passwd** ; which then asks for a new password for ROOT without having to enter whatever it used to be!  This is why anyone who has physical access to a Linux box can be root!!!

The Starman.

---

### Post by brainstuff on 2005-02-25
Thanks for the replies chaps. I have a feeling that seeing he is at Newbie Level 1, a full re-install is actually going to be a lot easier :p

(I'm only at newbie level 2 or maybe 3 so far so I doubt I could talk him through that :))

---

### Post by Blaze1024 on 2005-02-26
[QUOTE=brainstuff]Hi folks
I burnt a friend of mine the Ubuntu CD for him to install, which he did  last night. Between the hours of 12-4am. 

Needless to say he wasn't exactly * compus mentis* at the time, and now he doesn't remember ever entering a password during setup, let alone what it was. This is user password NOT root.

Is his only recourse to re-install from scratch or is there any way he can reset something to get back in?

By the way, I am not talking about myself in the third person to save embarrassment, this is actually true  :p[/QUOTE]


I also ran into this problem. ubuntu did not ask your friend for a Root password as the root account is disabled by default have your friend log in with his account and then follow the instructions on this page.. It always helps to read the FAQ first Its a lot easer then ](*,)  to solve a problem   

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root) 

Best Regards
Dan

---

