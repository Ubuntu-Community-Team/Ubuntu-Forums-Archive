---
title: "Update Manager not working"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ridgeone on 2008-02-23
I'm a noob. Tried 6.06 LTS last year and went back to XP. I enjoyed the Ubuntu experience but for work I needed XP. Now I was ready to try again so I installed 7.10 fresh on a new drive. Flawless install. So next thing I do is try to update using the Update Manager. When I click "install" it doesn't work - at all. This is what I get - [[IMG]http://img295.imageshack.us/img295/2175/screenshotwk3.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshotwk3.png)
Any thoughts? Any scripts I can try? Thanks.

---

### Post by Pumalite on 2008-02-23
At the Terminal:
sudo aptitude update
sudo aptitude upgrade

If you want to install software, use System>Administratin>Package Manager(Synaptic)

---

### Post by jeffus_il on 2008-02-23
Seems that you are lacking permission to do the requested update. Run the user manager and make sure that your user has administrative rights. Also try > sudo update-manager in a terminal

---

### Post by zvacet on 2008-02-23
Do you use synaptic with your first account witch you made during install?That one should have admin privileges and that is synaptic telling you (that you don´t have them).If you are trying to use synaptic as &#733;normal&#733;&#733;user (with no admin privileges) synaptic will not work.Only admin may install,uninstall.... and do other things witch require admin privileges.

---

### Post by ridgeone on 2008-02-23
Ok. Nothing happens when I enter commands in the terminal. For example, Pumalite, when I enter those commands and press enter nothing happens. It just returns to another line. I am using the only account I created on this machine. Can I log in as root from the login splash screen? The update manger asks me for the administrator password but it's when I enter it is when I get that error message. When I try to click on the install button again it just checks for updates again. I think I'm going to reformat and try installing again unless anyone can come up with anything.

---

### Post by taurus on 2008-02-23
What's the output of this command from a terminal?

```
id
```
You need to belong to group admin if you want to use sudo/gksudo.

---

### Post by ridgeone on 2008-02-23
easyrhino@Variable:~$ id
uid=1001(easyrhino) gid=1001(easyrhino) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),1001(easyrhino)
easyrhino@Variable:~$

---

### Post by ridgeone on 2008-02-23
Then I tried this for the heck of it:
easyrhino@Variable:~$ sudo ID
[sudo] password for easyrhino:
easyrhino@Variable:~$ apt-get install flash
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
easyrhino@Variable:~$

---

### Post by taurus on 2008-02-23
> **ridgeone said:**
> easyrhino@Variable:~$ id
uid=1001(easyrhino) gid=1001(easyrhino) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),1001(easyrhino)
easyrhino@Variable:~$

You are NOT the original user that was created during the installing process.  That user is usually an ID 1000, not 1001.

You need to add yourself to group admin first before you can use sudo/gksudo.  Boot into recovery mode from GRUB menu and at the prompt, run

```
useradd admin easyrhino
id easyrhino
shutdown -r now
```
You should see group admin from the output of the second command.

---

### Post by ridgeone on 2008-02-23
No dice. Same thing.

---

### Post by taurus on 2008-02-23
Edit /etc/group from the recovery mode

```
nano -Bw /etc/group
```
and add easyrhino to the end of group admin, near the end of the file.  Save it with <Ctrl>o and exit with <Ctrl>x.  

Then reboot.

```
shutdown -r now
```

---

