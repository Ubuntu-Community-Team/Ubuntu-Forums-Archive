---
title: "Pre-Upgrade Help"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by Freddie on 2005-10-23
I want to upgrade to Breezy. So, first like the guide said I typed in:
sudo apt-get install ubuntu-base ubuntu-desktop
But I got the message:
```
freddie@macserv:~$ sudo apt-get install ubuntu-base ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
ubuntu-base is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: cupsys but it is not going to be installed
                  Depends: cupsys-driver-gimpprint but it is not going to be installed
                  Depends: xpdf but it is not going to be installed
E: Broken packages
```
Can someone please tell me what is wrong and what I need to do to fix it.
Thanks for all of your help.

---

### Post by swerner on 2005-10-23
Have you edited /etc/apt/sources.list and changed all the "hoary" labels to "breezy"?  You will then need to do an 'apt-get update'.

---

### Post by Freddie on 2005-11-02
Sorry for brining this topic back up but I have been away for a while. Now, I am trying to do: "freddie@macserv:~$ sudo apt-get install ubuntu-base ubuntu-desktop" which is under the pre-upgrade section of then install guide, before the part about changing the respostories. So, what should I do? Do I go ahead with the install?

---

### Post by swerner on 2005-11-02
[QUOTE=Freddie]So, what should I do? Do I go ahead with the install?[/QUOTE]

Ok, so you have done the Pre-upgrade part, even though part of it failed you can still continue.  The errors are minor and will probably be fixed after the upgrade.

I recommend following the steps in the "apt-get" section of the breezy upgrade guide and use the sample sources.list.  In the last part of the "apt-get" section you will see the 'apt-get update' and 'apt-get upgrade' commands, it is safe to run these.  The first command will not take that long compared with the second command. 

Report back if you have any problems, and your success as well.  Hopefully just the latter.

---

### Post by Freddie on 2005-11-02
I do not think I have done the pre-upgrade part, as when I try it do it it tells me that things need to be installed but that they are being held back.

---

### Post by swerner on 2005-11-02
What errors do you get when you try to do the preupgrade?

---

### Post by Freddie on 2005-11-04
i get these errors:
```

freddie@macserv:~$ sudo apt-get install ubuntu-base ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
ubuntu-base is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: cupsys but it is not going to be installed
                  Depends: cupsys-driver-gimpprint but it is not going to be installed
                  Depends: xpdf but it is not going to be installed
E: Broken packages

```
Hope that helps.

---

### Post by swerner on 2005-11-05
I wouldn't worry about the errors too much. They are minor dependancy errors which should be fixed with dist-upgrade.  So I recomend to continue with the upgrade as I mentioned earlier.

---

