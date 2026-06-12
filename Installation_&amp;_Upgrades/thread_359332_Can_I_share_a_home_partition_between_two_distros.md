---
title: "Can I share a home partition between two distros?"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by Peepsalot on 2007-02-11
I have a Fedora Core 5 on a laptop of mine, and I want to put Ubuntu on there as well.  I would like to be able to dual boot these two OS's and have them share a home partition.  The problem is  that my permissions are different between the two distros even though I use the same username.

Someone told me that the problem is that my GIDs are different, but I'm not sure what to do about that, and I couldn't get any further help out of them.

---

### Post by unbuntu on 2007-02-11
> **Peepsalot said:**
> I have a Fedora Core 5 on a laptop of mine, and I want to put Ubuntu on there as well.  I would like to be able to dual boot these two OS's and have them share a home partition.  The problem is  that my permissions are different between the two distros even though I use the same username.

Someone told me that the problem is that my GIDs are different, but I'm not sure what to do about that, and I couldn't get any further help out of them.

I'm having the same question.  I have Ubuntu and Sabayon sharing one /home and things get ugly when I use the same user name for both distros.  Now I use different user names and they seem to co-exist pretty well.

---

### Post by DavidTangye on 2007-02-12
Its a bad idea to try to share homes of a same-named user between different instances of linuxes, even say Ubuntu Dapper and Edgy. The reason is that the versions of the apps, as well as the set of apps, is likely to be not the same, so personal config files, eg stored in $HOME/.(appname) etc, might need to be different in content or format in some cases.
You are better to have distinct homes, and each to link to a common directory, eg $HOME/MyStuff -> at say /var/local/(username)MyStuff for your general data files.

---

### Post by mr.v. on 2007-02-12
To my knowledge, most UNIXs and linux distros determine who owns the file based on the actual UID/GID NOT name. The name is correlated to the UID by checking the /etc/passwd file where it finds whose name correlates with the UID/GID and if they have permission or not.

Therefore, you need to make sure that not only are the two users in both distributions have the same name but that their GID and UID are identical. Find out what the username/UID/GID is for one distribution (say fedora) and then when you boot to ubuntu use **adduser** and specify the same username and UID then make sure  they belong to a group with the same GID (but this is less critical than the same UID).

Still there are plenty of hidden .config files/settings that are typically stored in the user's home directory that may conflict between the two distributions...

---

### Post by moon2js on 2007-04-15
> **DavidTangye said:**
> Its a bad idea to try to share homes of a same-named user between different instances of linuxes, even say Ubuntu Dapper and Edgy. 

Does this apply to upgrades as well? Like if you upgrade from Edgy to Feisty via via synaptic et al.?

---

