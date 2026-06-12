---
title: "Setting up sshd"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by terminator14 on 2008-05-08
I'm a bit new here so I'm not sure if this is the right category for my post, but here's my problem:

I'm running Ubuntu 8.04 and just installed OpenSSH from the main website (OpenSSH 5.0p1) - the portable one. I'm pretty sure that installs both ssh-client and ssh-server. After compiling and installing the package, when I run

```
sshd
```

I get

```
sshd re-exec requires execution with an absolute path
```

I did a little digging online and found that the solution is rather simple, but the paths that they use do not seem to match mine. 

Here an example of a forum post with the solution:

[http://www.linuxforums.org/forum/yoper-linux-help/12716-ssh-problems.html](http://www.linuxforums.org/forum/yoper-linux-help/12716-ssh-problems.html)

```
cat /etc/init.d/template |sed 's/PROGRAM/\/usr\/sbin\/sshd/g' >/etc/init.d/sshd
```

but all I get when I run this is:

```
cat: /etc/init.d/template: No such file or directory
```

How do I find what directory is the right one, and where in that code do I write that in?

---

### Post by StOoZ on 2008-05-08
I used to do it with this guide:
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by terminator14 on 2008-05-08
> **StOoZ said:**
> I used to do it with this guide:
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

I was looking for a good OpenSSH guide, thanks.

---

### Post by Vivaldi Gloria on 2008-05-10
```
sshd re-exec requires execution with an absolute path
```

means that instead of

```
sshd
```

you should write

```
/usr/sbin/sshd
```

At least that is where sshd is in my Gutsy & Hardy computers. But I installed it using synaptic and I don't know if it makes a difference.

---

### Post by DBrocks on 2008-05-10
install using "apt-get"

```
apt-get install openssh-server
```
Then it should run automatically.

---

### Post by Johnsie on 2008-05-10
AS drbocks said, you can do apt-get install to get it. On the server computer you should do:

> sudo apt-get install openssh-server

Once it's installed on the server you go onto the client computer and do:

Install the client:
> sudo apt-get install openssh-client


To Connect to your server:

> ssh 192.168.1.110 
(where 192.168.1.110 is the ip of your server)
or

> ssh steve@192.168.1.110 

where the ip address of the machine you want to connect to is 192.168.1.110 and the username you want to access on that machine is steve.

It's very easy and quite handy sometimes. Right now I'm actually using it to upgrade my server to Hardy Heron.


If you're using Windows on your client you can connect by using a program called Putty or with the Windows version of Openssh client.

---

### Post by DBrocks on 2008-05-10
and also do 
```
apt-get install openssh-client
```

---

### Post by Vivaldi Gloria on 2008-05-10
> **DBrocks said:**
> install using "apt-get"

```
apt-get install openssh-server
```
Then it should run automatically.

I installed openssh-server using the synaptic and sshd doesn't start unless I start it by

```
/usr/sbin/sshd
```

Is there a way to start it automatically?

---

### Post by Johnsie on 2008-05-10
hmmm thats starge that it doesn start automatically on boot... I'm looking for how I have gotstuuf to run at boot time and should be able to give you an answer in a few minutes.

---

### Post by DBrocks on 2008-05-10
you mean on boot?

---

### Post by Johnsie on 2008-05-10
ok... Try this:


> sudo nano /etc/rc.local 

end then add this to the bottom:
> 
cd /usr/sbin &
./sshd &
exit 0

Hopefully this should make it autostart at boot time. Let me know if it works for you

---

### Post by Vivaldi Gloria on 2008-05-10
> **DBrocks said:**
> you mean on boot?

Yes. Everytime i boot my computer I have to start sshd manually.

---

### Post by Vivaldi Gloria on 2008-05-10
> **Johnsie said:**
> Try this (...) Hopefully this should make it autostart at boot time. Let me know if it works for you

Johnsie, It worked! Thanks a lot.

---

### Post by Johnsie on 2008-05-10
You're welcome. Have fun :-)

---

### Post by terminator14 on 2008-05-16
Thanks for all your responses guys and sorry I haven't been replying to the help on my own thread but I have recently had tons of homework and haven't been able to have fun with my linux box at all.
Anyway:

> **DBrocks said:**
> install using "apt-get"

```
apt-get install openssh-server
```
Then it should run automatically.

I tried that, and it did work, running sshd without problems it would seem, but the only thing I wasn't happy about was that it seemed to be the old version of ssh. I thought it might have security holes or something that were fixed in the new one so I compiled the new one after downloading it from the site and couldn't get it to run. I guess for now I'll just use the old version until I get a break from homework to look into the matter again, but since there's only a month left before the end of the school year, and the finals are coming up, I don't think that will be anytime soon. Thank for your help anyway guys.

UBUNTU RULES!!!

---

