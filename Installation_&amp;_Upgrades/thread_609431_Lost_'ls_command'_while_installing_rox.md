---
title: "Lost 'ls command' while installing rox"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by meretricis on 2007-11-10
Alright, I've finally gone and done something warranting everyones help. 
Quick synapses so you know where I'm coming from, just got into linux about 4 days ago to revive a Pentium III 128RAM Toshiba Satellite Pro4600 with the most lightweight and efficient combination of software I could understand and t hen try to install. So far, It's all clicking in my head I'm happy to say and I've been fortunate enough not to cause such a serious problem as to be right screwed, save for now.
I'm running ubuntu/xubuntu fluxbox and trying to install rox.. this is where I ran into the mud.

I installed zeroinstall-injector, then downloaded rox with:
$ 0alias rox [http://rox.sourceforge.net/2005/interfaces/ROX-Filer](http://rox.sourceforge.net/2005/interfaces/ROX-Filer) 

as stated on their website: [http://roscidus.com/desktop/Ubuntu](http://roscidus.com/desktop/Ubuntu). Now it also says that after entering the above command it said "(it may prompt you to create a bin ("binary") directory for the script; follow the instructions)"
 So after I install everything I'm greeted with this:
mkdir ~/bin
export PATH=$HOME/bin:$PATH

I assume I'm supposed to execute these, so I type them in and them BAM! my ls command no longer works and my nano isn't either. I don't want to know what else, but I search and find out I've mucked up my $PATH. 
I don't know $PATH yet, I understand it holds my commads, such as ls and I've gone and exported it to who knows where. nice huh!

So, I %echo$PATH, the return is this.
bash: fg: %echo/home/anosis/bin:/home/anosis/bin::/usr/local/bin: no such job

now I think it's important to say that I executed the the export command this way as well:
export PATH=$HOME/bin: $PATH

this way seemed to have an impact.

NOw before you start shaking your heads lol! note that I executed the export command AFTER receiving this on trying to start rox:

/home/<user>/.cahce/0install.net/implementations/sha1new=bcb7bacfd7so.6:version 'GLIBC_2.4' not found (required by /home/<user>/.cachefb/ROX-Filer/ROX-Filer)


so yeah, could you kind people help me get my ls command back. And perhaps help rox working? EItherway, if I'm messed this up good I'm fine with restarting, so tell it to me straight doc. 

-meretricis

---

### Post by taurus on 2007-11-10
If you only run it from a terminal, just close that terminal and open another one.  Then, the new terminal will go back to the default PATH.  For future references, you should have done

```
export PATH=$PATH:~/bin
```

---

### Post by meretricis on 2007-11-11
Wow! I was expecting the worse and all I had to do was close my terminal lol!! That's awesome, here I was thinking I'm covering all my bases, googling, forum searching, all before I dare write a post and I neglected to just close/restart.
Actually, I think the reason I hadn't was out of fear for a freeze.

Nontheless, thank you Taurus.

as for the PATH command, am I to execute that after installing rox? I tried it just now and received  : not a valid identifier

---

### Post by taurus on 2007-11-11
Normally, you would have these two lines in your ~/.bashrc

```
PATH=$PATH:~/bin
export PATH
```
so you don't have to set your path from a terminal each time you open it.  It will read in automatically.

Are you using /bin/bash?

```
finger
```

---

### Post by meretricis on 2007-11-11
neither it seems? I executed finger and only my name login time and tty pts/0 showed up?

what does this mean?

---

### Post by meretricis on 2007-11-11
While I have veteran of Linux online, may I ask. As I mentioned before about reviving my P3 laptop here and trying to find the most efficient software to run it so it's 'actually' fast. What would you recommend?

I'm at Xubuntu/fluxbox/soon to be rox, what do you think of Fluxbuntu? Is it worth it, thesereally slimmed down distros of linux? Do I still have the ability to grow in knowledge or will I hit limitations?
YOur opinion please.

---

### Post by taurus on 2007-11-11
> **meretricis said:**
> neither it seems? I executed finger and only my name login time and tty pts/0 showed up?

what does this mean?

The whole output would be nice.

---

### Post by taurus on 2007-11-11
> **meretricis said:**
> While I have veteran of Linux online, may I ask. As I mentioned before about reviving my P3 laptop here and trying to find the most efficient software to run it so it's 'actually' fast. What would you recommend?

I'm at Xubuntu/fluxbox/soon to be rox, what do you think of Fluxbuntu? Is it worth it, thesereally slimmed down distros of linux? Do I still have the ability to grow in knowledge or will I hit limitations?
YOur opinion please.

Either Xubuntu or Fluxbuntu would be fine for your old laptop.  Just skip the fancy stuff and your laptop should be fine.

---

### Post by meretricis on 2007-11-11
Login         Name                    Tty      Idle     Login Time     Office     Office phone
<user>     <userfullname>    Pts/0             NOv 10 21:53  (:0.0)

---

### Post by taurus on 2007-11-11
What about?

```
tail /etc/passwd
```

---

### Post by meretricis on 2007-11-11
could I install fluxbuntu from where I'm at and get rid of the excess I havefrom the other distro installs?
It might sound like a crazy question, but with what I've worked in these last few days, I believe in linux miracles;)

---

### Post by taurus on 2007-11-11
What did you install on your machine before:  Ubuntu, Kubuntu, or Xubuntu?

You can remove Kubuntu & Xubuntu with this, [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome).

Or you can remove Ubuntu & Xubuntu with this, [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde).

---

### Post by meretricis on 2007-11-11
is there a cut and paste option in terminal? this is a long one.

---

### Post by taurus on 2007-11-11
Highlight with the left mouse and paste with the middle or both left and right at the same time if you have only two-button mouse.  The small middle roller is used for paste if you have that.

---

### Post by meretricis on 2007-11-11
```
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
cupsys:x:100:106::/home/cupsys:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:106:111:Gnome Display Manager:/var/lib/gdm:/bin/false
user:x:1000:1000:userfullname,,,:/home/user:/bin/bash
```

---

