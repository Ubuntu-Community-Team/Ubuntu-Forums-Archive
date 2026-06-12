---
title: "Running Calibre No write access message"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2017-08-31
Please see that thread for background on how I installed Calibre [https://ubuntuforums.org/showthread.php?t=2368617&page=2](https://ubuntuforums.org/showthread.php?t=2368617&page=2)

I did sudo apt-get update
Sudo apt-get upgrade

Then tried again to run calibre and got ```
No write acces to /home/snukies/.config/calibre using a temporary dir instead
Illegal instruction (core dumped)


```

---

### Post by ajgreeny on 2017-08-31
Right click on the folder **.config/calibre** in your file manager and let's see what permissions it has; there should be no problems for you writing to that folder but for some reason you have no write access to it.
I am not sure whether that is your main problem but it is rather suspicious, and not what is expected or correct.

---

### Post by Jorhel on 2017-09-02
OK I checked the permissions are as follow
Owner root (root) read and write
Group root none
Others none

I have to users on my computer Helene/Snukies (Admin) and Kids/kids (custom) Both belonging to the group snukies and the group kids.
I remember having issues with the groups  when I started with 14.04. Ideally I want to be able to acces everything on the computer including the kids folders but have them accessing only theirs and of course not let them install stuff.
I just scrolled through the list of groups available on the computer and ticked myself in the group root. That does not happen to have changed anything with the permissions in calibre.

---

### Post by Impavidus on 2017-09-02
That directory shouldn't be owned by root. It should be owned by your ordinary user, snukies. Best to fix the group too. Use```
sudo chown -R snukies:snukies ~/.config/calibre
```Maybe the first time you ran calibre, you ran it with sudo. That would have created the .config/calibre directory with root as the owner.

You can use sudo, so you have access to the kids' directories, but better only do that with sudo as root in an emergency. If you routinely do stuff in the kids' directories, you could do so by making sure the kids group has write permissions and you belong to the kids group. The kids could lock you out by removing permissions for the group, but you can fix that using sudo.

Don't put yourself in the root group. That could cause even more trouble.

---

### Post by Jorhel on 2017-09-02
> **Impavidus said:**
> That directory shouldn't be owned by root. It should be owned by your ordinary user, snukies. Best to fix the group too. Use```
sudo chown -R snukies:snukies ~/.config/calibre
```Maybe the first time you ran calibre, you ran it with sudo. That would have created the .config/calibre directory with root as the owner.

You can use sudo, so you have access to the kids' directories, but better only do that with sudo as root in an emergency. If you routinely do stuff in the kids' directories, you could do so by making sure the kids group has write permissions and you belong to the kids group. The kids could lock you out by removing permissions for the group, but you can fix that using sudo.

Don't put yourself in the root group. That could cause even more trouble.

I did that and got
 ```
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ sudo chown -R snukies:snukies ~/.config/calibre
[sudo] password for snukies: 
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ calibre
Illegal instruction (core dumped)

```
When I go to the calibre folder the owner and group has been change to snukies and I changed the group permission from none to read and write but still got the error message above.

---

### Post by Impavidus on 2017-09-03
The "No write access" message is gone, so the lesser of your problems is solved. The other message suggests that your version of calibre wasn't properly compiled for your hardware. I use the repository version of calibre (2.75.1), which is good enough for me, but maybe someone from your other thread who installed from their site has some ideas.

---

