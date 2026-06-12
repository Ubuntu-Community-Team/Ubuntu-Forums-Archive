---
title: "Samba problem"
date: 2009-11-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-11-29
Hi

I am having a problem with Samba in Lucid, though it may not be entirely Lucid based as I have some of the symptoms as
[http://ubuntuforums.org/showthread.php?t=1296111](http://ubuntuforums.org/showthread.php?t=1296111)
(Thread: A bit late, I know, but Karmic Samba "fail" issues.... in Karmic Koala testing and discussions)

What happens:

Whenever I try to see computers in workgroup (either through nautilus or gnome-commander) I am prompted for a password (nautilus asks for a password for the logged in user, domain = workgroupname, gnome-commander for 'guest', no domain specified). No matter what I enter (or leave the password field blank) I am reprompted to enter a password.

It seems to take both (nautilus and gnome-commander) quite some time to display the workgroup name in the first place.

I have exactly the same smb.conf on my Karmic box, which behaves as I would expect: i.e. on double clicking the workgroup in nautilus I get to see a list of computers in the workgroup.

Something which is probably significant is that when I select 'Network' from 'Places', on the Karmic box I see a list of computers as well as 'windows network'. When I select 'Network' from 'Places', on the Lucid box I only see 'windows network.

I can connect directly to another of the computers using 'connect to server', selecting 'windows share'  as 'service type' and entering the computer name.

Can anyone help?

Other things which may be of note in all the various checking, uninstalling etc. I have done to try to fix this is that shares added via nautilus (using 'sharing options' from 'nautilus share plugin' &#8211; which I don't remember having to install before) don't appear in 'system-config-samba'. Also, I have no smbusers file in /etc/samba, although on my Karmic box this exists but is 0 bytes.

Also:
me@lucidbox:~$ smbclient -L lucidbox
Enter me's password: 
Anonymous login successful
Domain=[xxx] OS=[Unix] Server=[Samba 3.4.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (lucidbox server (Samba, Ubuntu))
	music           Disk      
Anonymous login successful
Domain=[xxx] OS=[Unix] Server=[Samba 3.4.3]

	Server               Comment
	---------            -------
	Vista-PC             
	lucidbox            lucidbox server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	xxx             Vista-PC
me@lucidbox:~$

---

### Post by scradock on 2009-11-29
Me too - haven't used Samba shares for a while, and now I get this stupid password prompt when I try to go from "Windows Network" to "workgroup". I installed "system-config-samba" (why would Samba come without a configuration tool??!!!) and checked my user status - sure enough there was a password that I couldn't read, so I had no idea what it was. I changed it to something I knew and that seemed to fix the problem. I haven't checked to see if I get full ability to browse the rest of my network yet...

HTH

---

### Post by scradock on 2009-11-29
Confirming that removing the passwords from the User details in system-config-samba does away with the password prompt entirely, as I would expect.

I also confirm that I have regained the ability to access other (Windows) machines and their shares.

---

### Post by Gilankzz on 2009-11-29
uninstall your samba in Synaptic PM

and then install again your samba

---

### Post by scradock on 2009-11-29
> **Gilankzz said:**
> uninstall your samba in Synaptic PM

and then install again your samba
Sounds like a good idea - programs with hard-to-find configuration settings are often improved by the sledge-hammer technique.

I spoke too soon, earlier - that worked in karmic (where I too was having apparently the same problem). In Lucid, trying to reset the (unknown) password in system-config-samba fails - the original (# of) stars reappear in the password fields after closing and reopening the user details dialog, even if I select and delete the whole string (x2).

It does look at the moment as if, in Lucid at least, the password is now pre-set (to an unknown value) and that the password store is not properly addressed by system-config-samba, so it can't be changed.

Any other ideas?

---

### Post by scradock on 2009-11-30
> **Gilankzz said:**
> uninstall your samba in Synaptic PM

and then install again your samba
Tried that - removed all samba-related programs and re-installed. Exact same symptoms.

I've filed a bug - launchpad #490201.

It seems that the password is pre-set, and the location it's stored in has been changed so that system-config-samba doesn't address it correctly.

Any ideas, anyone?

---

### Post by ubername on 2009-11-30
> **Gilankzz said:**
> uninstall your samba in Synaptic PM

and then install again your samba

I have uninstalled and reinstalled samba and anything with samba in the name or description (pretty much - I left libwclient0 and libsmbclient) many times - I even tried samba4, but only briefly as I couldn't get that to work either so I thought to stick with a more mature version.

I have just tried the 'delete password' work around and it hasn't (worked around!).

---

### Post by ubername on 2009-11-30
Added some requested info to launchpad #490201
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/490201)

---

### Post by cariboo on 2009-11-30
I've just been playing with connecting to my server, and enabled the location bar in nautilus. It seems that nautilus is adding an extra / when trying to connect to the sever. I see:

```
smb:///
```

when trying to connect to the server using either Places-->Network or Places-->Connect to Server. Once I remove the extra slash, things work as expected. Is anyone else seeing this?

---

### Post by ubername on 2009-11-30
> **cariboo907 said:**
> I've just been playing with connecting to my server, and enabled the location bar in nautilus. It seems that nautilus is adding an extra / when trying to connect to the sever. I see:

```
smb:///
```

when trying to connect to the server using either Places-->Network or Places-->Connect to Server. Once I remove the extra slash, things work as expected. Is anyone else seeing this?

Yup, good spot. I am seeing the extra slash (network:/// then smb:///

but unfortunately removing it does not change the password prompt behaviour. (and still get the same in gnome-commander - I can't see the actual string it is creating so don't know if there is an extra slash.)

---

### Post by cariboo on 2009-11-30
I guess this is just a work around, but when I remove one of the slashes and enter the server name, it then brings up the password prompt. I enter my password and username on the sever and I can then connect to the share.

I just looked in karmic and see the same behaviour the three slashes, but it connects to the shares properly and excepts the password like it should.

---

### Post by ubername on 2009-11-30
> **cariboo907 said:**
> I guess this is just a work around, but when I remove one of the slashes and enter the server name, it then brings up the password prompt. I enter my password and username on the sever and I can then connect to the share.

I just looked in karmic and see the same behaviour the three slashes, but it connects to the shares properly and excepts the password like it should.

Thanks, that works if I know the name of the remote computer, but I actually want to see the names of the computers in the workgroup. Is there a command that goes something like smb://<workgroup> ?

---

### Post by garvinrick4 on 2009-12-02
Have 2 boxes: All were working networks. 1 box with Vista/9.10 and 1 box with  7/9.10/9.10.   Upgraded 1 of the 9.10 to 10.04 and the 10.04 go's to Windows network to workgroup to password. Cannot find salution all looks same as other 2  Karmic
installs. All other networks show all partitions and a window network icon that go's to a 
workgroup and go's to partitions. Lucid sees workgroup and a password?

Same problem as start of Thread.  Seems to be a bug will go to launchpad and see what priority it is. 

Maybe one of you can come up with fix, I have tried and cannot. Post if you do.

---

### Post by ubername on 2009-12-02
Update: Just installed updates, including new kernel 2.6.32-6 if that's at all relevant, and now I don't see my workgroup via nautilus - windows network!

Edit - Hmm... I can now see the workgroup name again.

---

### Post by Gina on 2009-12-02
I only see the Windows Network too.  No Linux devices can be found :(

---

### Post by scradock on 2009-12-02
> **ubername said:**
> Update: Just installed updates, including new kernel 2.6.32-6 if that's at all relevant, and now I don't see my workgroup via nautilus - windows network!

Edit - Hmm... I can now see the workgroup name again.
Hmmm - I have the new kernel (32-6) and I see Workgroup in Nautilus, but I get the password prompt as before. No known password works.

Two problems:  1 - something is setting a password, which I don't know.

2 - the system-config-samba GUI cannot change that password, as it can in karmic.

---

### Post by garvinrick4 on 2009-12-03
[https://bugs.launchpad.net/ubuntu/+s...ba/+bug/490201]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/490201")


There is bug in launchpad let em Know so they get it off the ground.
It is in a low urgency right now.

---

### Post by garvinrick4 on 2009-12-04
Samba has considered it a nautilus problem. But a problem.

This really isn't a samba bug, as following the steps on this page:

[https://wiki.ubuntu.com/DebuggingSamba](https://wiki.ubuntu.com/DebuggingSamba)

everything works as it should.

smbclient -L //willy
Enter my password: <press enter >
Anonymous login successful
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    Movies          Disk      Movies & TV Shows
    Music           Disk      Music
    Documents       Disk      Documents
    Stuff           Disk      Everything Else
    Iso             Disk      Mounted iso's
    IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
Anonymous login successful
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

    Server               Comment
    ---------            -------
    COLLECTOR            
    MCLEESE              
    RISKY                XP Computer
    WILLY                willy server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    APLUS                WILLY

me@chilanko-lucid:~$ smbclient //willy/stuff
Enter e password: <enter password of user on server>
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]
smb: \> dir
  .                                   D        0  Wed Dec  2 19:58:05 2009
  ..                                  D        0  Wed Nov 11 20:21:27 2009
  Downloads                           D        0  Fri Jul 17 00:55:34 2009
  stuff                               D        0  Tue Aug 18 12:58:19 2009
  restore                             D        0  Tue Dec  1 20:28:04 2009

the above results indicate to me, that samba is working as it should.
the problem seems to me to be with nautilus.

-- 
samba fails to open shares because of fixed unknown password
[https://bugs.launchpad.net/bugs/490201](https://bugs.launchpad.net/bugs/490201)
You received this bug notification because you are a direct subscriber
of the bug.

Status in “samba” package in Ubuntu: Confirmed

Bug description:
Binary package hint: samba

In Lucid, the samba shares that should be accessible through nautilus cannot be 
opened because clicking on WORKGROUP opens a password dialog. Investigation 
using system-config-samba shows an unreadable password for the (only) user, 
which cannot be changed or deleted (as it could be in Karmic).

---

