---
title: "gksudo in 18.04?"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2018-06-04
Hello,

I've just upgraded from 16.04 to 18.04 and find ```
gksudo nautilus
``` no longer works.  Can someone advise me what to use instead for a root file manager?

Thanks in advance.

---

### Post by monkeybrain20122 on 2018-06-04
gksudo is gone
```

Try sudo -H nautilus
```

or

```
pkexec nautilus
```

for the second one you may need to install nautilus-admin

---

### Post by mlnease on 2018-06-04
-H nautilus did it--thanks!

---

### Post by vanadium on 2018-06-05
"pkexec nautilus" also works. You may prefer that. Yes, "sudo -H" works, but so does "sudo". However, either of the two last approaches might cause issues with your graphical software, "sudo -H" less likely than sudo, may still cause issues. To play it fully safe, use pkexec. It is designed to start graphical applications as root.

---

### Post by mlnease on 2018-06-05
> **vanadium said:**
> "pkexec nautilus" also works. You may prefer that. Yes, "sudo -H" works, but so does "sudo". However, either of the two last approaches might cause issues with your graphical software, "sudo -H" less likely than sudo, may still cause issues. To play it fully safe, use pkexec. It is designed to start graphical applications as root.

Thanks for this--will do.

Hang on:

```
mn@mn-OptiPlex-745:~$ pkexec nautilus
Unable to init server: Could not connect: Connection refused

(nautilus:17326): Gtk-WARNING **: 11:08:39.296: cannot open display: 
mn@mn-OptiPlex-745:~$ sudo pkexec nautilus
[sudo] password for mn: 
Unable to init server: Could not connect: Connection refused

(nautilus:17337): Gtk-WARNING **: 11:08:57.905: cannot open display: 
mn@mn-OptiPlex-745:~$ 
```
Am I missing something?  Thanks and in advance.

---

### Post by Morbius1 on 2018-06-05
A lot of people keep suggesting "pkexec nautilus" but I can't get it to work either.

Anyhoo the fella that took gksu away suggests using admin:// instead. As in:
```
gedit admin:///etc/fstab
```
```
nautilus admin://
```
[COLOR=#0000cd]*Of course you can always "trade up" to Xubuntu where it's a one-t-one substitution of pkexec for gksu:*[/COLOR]
```
pkexec mousepad /etc/fstab
```
```
pkexec thunar
```

[COLOR=#0000cd]**EDIT**[/COLOR]: This is the fella that took gksu away in case you want to send him flowers or something: [URL="https://bugs.launchpad.net/ubuntu/+source/umit/+bug/1740618"]https://bugs.launchpad.net/ubuntu/+source/umit/+bug/1740618
And why pkexec works in Xubuntu and not in Gnome seems to be some Gnome thing?
[/URL]

---

### Post by monkeybrain20122 on 2018-06-05
> **mlnease said:**
> Thanks for this--will do.

Hang on:

```
mn@mn-OptiPlex-745:~$ pkexec nautilus
Unable to init server: Could not connect: Connection refused

(nautilus:17326): Gtk-WARNING **: 11:08:39.296: cannot open display: 
mn@mn-OptiPlex-745:~$ sudo pkexec nautilus
[sudo] password for mn: 
Unable to init server: Could not connect: Connection refused

(nautilus:17337): Gtk-WARNING **: 11:08:57.905: cannot open display: 
mn@mn-OptiPlex-745:~$ 
```
Am I missing something?  Thanks and in advance.


To use pkexec you need a policy file. If it is not installed by default you have to make one yourself or download one from a ppa, this is just ridiculous. With nautilus though installing the package nautilus-admin will get you the policy file but it won't work with gedit, for example.

sudo -H is ok.

---

### Post by monkeybrain20122 on 2018-06-05
> **Morbius1 said:**
> A lot of people keep suggesting "pkexec nautilus" but I can't get it to work either.

Anyhoo the fella that took gksu away suggests using admin:// instead. As in:
```
gedit admin:///etc/fstab
```
```
nautilus admin://
```
[COLOR=#0000cd]*Of course you can always "trade up" to Xubuntu where it's a one-t-one substitution of pkexec for gksu:*[/COLOR]
```
pkexec mousepad /etc/fstab
```
```
pkexec thunar
```


With  admin:// you need the full path following it.

for example

```
cd /etc

gksudo gedit fstab 
```

would work

but
```
cd /etc

gedit admin://./fstab 
```

or variations won't

has to be

```
gedit admin:///etc/fstab
```

---

### Post by Morbius1 on 2018-06-05
Oh, and btw there is a curious little bug with using admin://.

The very first time you use it -- as in **nautilus admin:// **you will be prompted for a password which is what you expect. When you hit enter you will be asked for a password again. Doesn''t happen any time after that in your session only at first use.

You gotta love Linux folks.

---

### Post by mlnease on 2018-06-05
Huh!  All a bit baffling to me but thanks anyway all.

---

### Post by vanadium on 2018-06-05
Indeed, now I see that I installed a policy file, which is why "pkexec nautilus" works for me. On [http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html) you will find a few lines of code that download policy files for gedit and nautilus, and copy them to the right location.

---

### Post by Morbius1 on 2018-06-06
And that is why pkexec works in Xubuntu out of the box without installing anything, downloading anything, or making any other adjustments to your OS. The equivalent of these files are already present in a new install.

---

### Post by mlnease on 2018-06-06
> **Morbius1 said:**
> And that is why pkexec works in Xubuntu out of the box without installing anything, downloading anything, or making any other adjustments to your OS. The equivalent of these files are already present in a new install.

This is a new install of Xubuntu 18.04 using (of course) xfce.  Here is my output from pkexec:

```
mn@mn-OptiPlex-745:~$ pkexec nautilus
Unable to init server: Could not connect: Connection refused

(nautilus:2617): Gtk-WARNING **: 08:50:40.619: cannot open display: 
mn@mn-OptiPlex-745:~$ sudo pkexec nautilus
[sudo] password for mn: 
Unable to init server: Could not connect: Connection refused

(nautilus:2628): Gtk-WARNING **: 08:51:00.655: cannot open display: 
mn@mn-OptiPlex-745:~$ 
```
Thanks for your time and attention.

[edit]  I installed PolicyKit files for Nautilus
```
wget https://raw.githubusercontent.com/hotice/webupd8/master/org.gnome.nautilus.policy -O /tmp/org.gnome.nautilus.policy
sudo cp /tmp/org.gnome.nautilus.policy /usr/share/polkit-1/actions
```
and for Gedit
```
wget https://raw.githubusercontent.com/hotice/webupd8/master/org.gnome.gedit.policy -O /tmp/org.gnome.gedit.policy
sudo cp /tmp/org.gnome.gedit.policy /usr/share/polkit-1/actions/
```

Pkexec works now for both.

Thanks for your time and attention.

---

### Post by Morbius1 on 2018-06-06
And what happens when you use Xubuntu's file manager:
```
pkexec thunar
```
Like I said Xubuntu already contains everything it needs to run pkexec against it's own native applications: /usr/share/polkit-1/actions/org.xfce.thunar.policy

[COLOR=#0000cd]**EDIT**[/COLOR]: And the one for mousepad which is Xubuntu's default text editor is here: /usr/share/polkit-1/actions/com.ubuntu.pkexec.mousepad.policy

---

### Post by mlnease on 2018-06-06
--and like I said, pkexec did *not* work in *my* new Xubuntu install until I installed PolicyKit as above.

pkexec thunar works presently.

Thanks again for your time and attention.

---

### Post by Morbius1 on 2018-06-06
You are missing the point of all this.[B] 

pkexec thunar[/B] works by default. It does not require any additions or modifications. That is a fact.

pkexec nautilus would not work because it's not a native XFCE application and it's not the default for Xubuntu.

Xubuntu is designed to be functional. For each application that you want pkexec to work a policykit "rule" must be added. Xubuntu added them for it's own applications. Gnome did not.

If you run Xubuntu from your install disk you can verify for yourself that pkexec thunar works by default.

---

### Post by mlnease on 2018-06-06
> **Morbius1 said:**
> You are missing the point of all this.[B] 

pkexec thunar[/B] works by default. It does not require any additions or modifications. That is a fact.


Yes, I've gathered that,  thanks.

> **Morbius1 said:**
> pkexec nautilus would not work because it's not a native XFCE application and it's not the default for Xubuntu.


That too.

> **Morbius1 said:**
> Xubuntu is designed to be functional. For each application that you want pkexec to work a policykit "rule" must be added. Xubuntu added them for it's own applications. Gnome did not.

If you run Xubuntu from your install disk you can verify for yourself that pkexec thunar works by default.

I'll gladly take your word for it.  Thanks again for your time and attention.

---

### Post by monkeybrain20122 on 2018-06-06
> **Morbius1 said:**
> You are missing the point of all this.

Xubuntu is designed to be functional. For each application that you want pkexec to work a policykit "rule" must be added. Xubuntu added them for it's own applications. Gnome did not.
.

That was exactly my point. It is ridiculous so if I don't use xubuntu or if I use xubuntu but want to use non xfce apps I would have to add each application to a policy file. It just encourages abusing sudo.

---

### Post by Morbius1 on 2018-06-06
I think that is exactly what will happen. People will start using sudo gedit all over the place.

I don't usually have many positive things to say about KDE but if you were going to implement this sort of thing they generally got the right idea. They used the macOS method.

I can edit a system file as an ordinary user but when I go to save it this happens:
[ATTACH=CONFIG]280007[/ATTACH]
Put in my sudo password and we are good to go.

Still no way to run kdesudo dolphin mind you but ...

---

### Post by TheFu on 2018-06-15
For editing files, **sudoedit** is easy and safe. set the EDITOR environment variable and sudoedit will honor it.

sudoedit works by copying the file to a temporary location, invoking the editor of your choice, you make edits under your own userid,  then it copies the file back and makes all the permissions like they were before.  2 parts (copy from and copy back) use elevated privileges.  gedit can be use, nano, vim, geany, eclipse, whatever, provided you have a GUI if you request a GUI editor.  Work across all systems that use sudo, so server, LXDE, LXQT,  Gnome2/3, KDE, and  all the others work fine too.

---

