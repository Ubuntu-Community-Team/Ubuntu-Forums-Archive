---
title: "Firewall and antivirus"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-11-12
I know some people will debate the need for a firewall and/or antivirus on non-Windows machines, which is perfectly OK.  However, does anyone know of good ones, or at least a good starting place for me to search.  Thanks in advance.

---

### Post by Dangertux on 2011-11-12
As far as firewalls go the netfilter/iptables kernel modules provide verbose firewall support. Here is a thread I created illustrating how to configure them using three different methods varying on your level of experience : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Also as far as AV goes, I haven't found a particularly good free AV solution. Some people swear by ClamAV in my opinion its a lot of false positives and not so great at detecting things it should. Avast! and AVG also have free linux products, but I've seen similar results from them.

Hope this helps

---

### Post by haqking on 2011-11-12
> **lm77054 said:**
> I know some people will debate the need for a firewall and/or antivirus on non-Windows machines, which is perfectly OK.  However, does anyone know of good ones, or at least a good starting place for me to search.  Thanks in advance.

N00b guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Do you need one:  [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

How to enable one: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

IN short yes you need a firewall, AV well the truth is there are no good ones in the Linux world for the domestic user and Linux is not highly targeted.

However this debate is done countless times if you head to the security discussions sub-forum.

Also read the links in my signature.

Cheers

---

### Post by lm77054 on 2011-11-12
> **Dangertux said:**
> As far as firewalls go the netfilter/iptables kernel modules provide verbose firewall support. Here is a thread I created illustrating how to configure them using three different methods varying on your level of experience : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Also as far as AV goes, I haven't found a particularly good free AV solution. Some people swear by ClamAV in my opinion its a lot of false positives and not so great at detecting things it should. Avast! and AVG also have free linux products, but I've seen similar results from them.

Hope this helps

 Thanks!  When I was "playing around" yesterday, before I help a friend setup a Windows App'd UBUNTU, I found that AVAST (I use it on Windows) had a LINUX version ([http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)), but when I tried to install it, I ran into problems.  Now looking closer, it might have been because of the comment of "The user interface requires GTK+ 2.x libraries."  I don't know what GTK+ is (yet), and it makes me wonder is that is the reason for the problem.  I'll experiment on this later.

---

### Post by lm77054 on 2011-11-12
> **haqking said:**
> N00b guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Do you need one:  [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

How to enable one: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

IN short yes you need a firewall, AV well the truth is there are no good ones in the Linux world for the domestic user and Linux is not highly targeted.

However this debate is done countless times if you head to the security discussions sub-forum.

Also read the links in my signature.

Cheers

 I'll take a look.  Thanks

---

### Post by nrundy on 2011-11-12
> **lm77054 said:**
> I know some people will debate the need for a firewall and/or antivirus on non-Windows machines, which is perfectly OK.  However, does anyone know of good ones, or at least a good starting place for me to search.  Thanks in advance.

You don't need to run Anti-Virus on your Linux (at least not for the foreseeable future). Running Anti-Virus is not recommended. Anti-Virus is a pathetic protection against malware anyway. It's a blessing to not need to use it. 

For Firewall, if you are comfortable with command-line use UFW. If you want a GUI, install and use GUFW. A sad fact though is that you can't control applications' internet connections via the firewall in linux :( You can control IP and port connections generally across all applications though.

---

### Post by Lars Noodén on 2011-11-12
> **nrundy said:**
> A sad fact though is that you can't control applications' internet connections via the firewall in linux :( You can control IP and port connections generally across all applications though.

I'm not sure where to look, but I think that capability might have been added to AppArmor in Oneiric.

---

### Post by Dangertux on 2011-11-12
> **nrundy said:**
> You don't need to run Anti-Virus on your Linux (at least not for the foreseeable future). Running Anti-Virus is not recommended. Anti-Virus is a pathetic protection against malware anyway. It's a blessing to not need to use it. 

For Firewall, if you are comfortable with command-line use UFW. If you want a GUI, install and use GUFW. A sad fact though is that you can't control applications' internet connections via the firewall in linux :( You can control IP and port connections generally across all applications though.


You can fine tune access to capabilities like networking or even certain aspects of networking UDP streaming, socket creation, broadcast etc, via mandatory access controls like SELinux or Apparmor (installed with Ubuntu by default)

The security stickies that are linked in this thread already provide decent documentation on apparmor.

As far as controlling application's activity with iptables, it is possible to some extent with netfilter/iptables to limit what an application can do by it's owner UID or GID, as well you can add additional fucntionality like string matching to iptables via addins like FWSnort.

So I would say between iptables and apparmor you have all you need to control whatever you need. Just my 2 cents.

---

### Post by nrundy on 2011-11-12
Guys, if the OP is asking about Anti-Virus on Linux he's obviously a newb. He's not going to know how to use apparmor/selinux. It's unlikely he's going to be able to learn how to use it. It's very advanced. Most users are dependent on developers to preconfigure these for them. But it is good that the user be aware of these security feature (app armor) even though he'll never "see" it.

Firewall is a great way for the user to gain control over the comings & goings on their computer. There's obviously a security/privacy component, but the primary advantage is control. Unfortunately this control is less than ideal on linux firewalls because of the lack of application control.

---

### Post by haqking on 2011-11-12
> **nrundy said:**
> Guys, if the OP is asking about Anti-Virus on Linux he's obviously a newb. He's not going to know how to use apparmor/selinux. It's unlikely he's going to be able to learn how to use it. It's very advanced. Most users are dependent on developers to preconfigure these for them. But it is good that the user be aware of these security feature (app armor) even though he'll never "see" it.

Firewall is a great way for the user to gain control over the comings & goings on their computer. There's obviously a security/privacy component, but the primary advantage is control. Unfortunately this control is less than ideal on linux firewalls because of the lack of application control.

hence the noob guy link in my post #3 [http://ubuntuforums.org/showpost.php?p=11449660&postcount=3](http://ubuntuforums.org/showpost.php?p=11449660&postcount=3)

and other links to allow them to follow a guide on how to become a little more secure as a noob

---

### Post by Dangertux on 2011-11-12
> **nrundy said:**
> Guys, if the OP is asking about Anti-Virus on Linux he's obviously a newb. He's not going to know how to use apparmor/selinux. It's unlikely he's going to be able to learn how to use it. It's very advanced. Most users are dependent on developers to preconfigure these for them. But it is good that the user be aware of these security feature (app armor) even though he'll never "see" it.

Firewall is a great way for the user to gain control over the comings & goings on their computer. There's obviously a security/privacy component, but the primary advantage is control. Unfortunately this control is less than ideal on linux firewalls because of the lack of application control.

 I quoted and replied to you, since you were the one who asked about application level control. 

That being said Apparmor isn't really that steep of a learning curve and if I was a new user asking questions I would be rather offended if people assumed I was too much of a "noob" to learn. That's why the information is there, so that when a user is ready, they can begin to learn.

---

