---
title: "KDevelop in Ubuntu 6.06?"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by mikeman on 2007-02-22
Hello,

What I've been trying to do for the last hours is just install KDevelop. I tried downloading it, but is says there are unresolved dependecies(kdelibs), those dependencies have other dependencies and so on. I'm pretty much lost and very tired of all this. I've been told to use "sudo apt-get install kdevelop", but it doesn't work. It says it can't find packate "kdevelop".

Is there anyone that can explain what I must do to get KDevelop to install? Thanks in advance.

---

### Post by Kateikyoushi on 2007-02-22
I just typed the following it would pull down 12 packages and I do not even have kde.

```
sudo aptitude install kdevelop
```

---

### Post by mikeman on 2007-02-22
Well, I did that and no dice. It says something like "no package found that fits name or description 'kdevelop'"

---

### Post by louieb on 2007-02-22
In Ubuntu (not kUbuntu)
System>Administration>Synaptic 

Search for **KDevelop ** package name there is KDevelop3. I marked it for install and it would have installed 
18 other packages. (KDE is not on this machine either). 
if the packages are not listed you should check you /etc/apt/sources.list  file to make sure the repositories are not commented out.

If you need to edit it the press Alt+F2 and enter
```
 gksudo gedit /etc/apt/sources.list
```

---

### Post by mikeman on 2007-02-22
Well, this is really strange.

I reinstalled Ubuntu, I think I've fixed the sources list, but not if I try to do "sudo apt-get update". I get an error, something like:

"Can't lock /var/lib/apt/lists/lock-open(11 Resource temporarily unavailable)"

I remember I didn't got that error hours ago. I can't see any open apps that may cause this. I've tried rebooting and I got the same thing. What's the problem  now?

---

### Post by mikeman on 2007-02-22
Ok, an update: I have killed some processes, and it worked. Except not really :)

What I get now with "sudo aptitude update" is:

Building tag database...Done
0%[Connecting to archive.ubuntu.com(1.0.0.0)]

Now, this "1.0.0.0" surely isn't correct, right? I know my internet is fine, in fact I can see "http://archive.ubuntu.com/" with my Firefox browser. So what's the problem here?

Thanks again.

---

### Post by Kateikyoushi on 2007-02-22
Do you use ipv6 ? I think that's the cause.

---

