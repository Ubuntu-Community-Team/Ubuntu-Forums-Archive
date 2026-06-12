---
title: "[SOLVED] admin programs wont work!"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-08-23
I got half an answer from a previous post but didn't get an answer to this part of my question. (i think it was missed) so I am posting it again. Hope thats okay.

Straight after a clean install of Hardy heron I cannot open any program requiring admin privileges. so I cannot install the required Nvidia drivers etc, which may account for the slowness of the OS right now. Anyone got a suggestion?

Booting into 2.6.24-19 I found that everything worked like -- mega slow, (made vista appear fast) and none of the processes requiring admin rights would actually open. ie I tried synaptic, and can see two titles in the bottom bar saying something like, opening syanptic and opening admin rights, and then Poof! they are gone and nothing happens. 

:(

---

### Post by iaculallad on 2008-08-23
> **tropdoug said:**
> I got half an answer from a previous post but didn't get an answer to this part of my question. (i think it was missed) so I am posting it again. Hope thats okay.

Straight after a clean install of Hardy heron I cannot open any program requiring admin privileges. so I cannot install the required Nvidia drivers etc, which may account for the slowness of the OS right now. Anyone got a suggestion?

Booting into 2.6.24-19 I found that everything worked like -- mega slow, (made vista appear fast) and none of the processes requiring admin rights would actually open. ie I tried synaptic, and can see two titles in the bottom bar saying something like, opening syanptic and opening admin rights, and then Poof! they are gone and nothing happens. 

:(

Try to post whatever displays when you issue the command below on your terminal:

```
cat /etc/hosts
```

---

### Post by tropdoug on 2008-08-23
```
127.0.0.1 localhost
127.0.1.1 desktop.DougsBox

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
doug@douglas-desktop:~$ 


```

---

### Post by iaculallad on 2008-08-23
> **tropdoug said:**
> ```
127.0.0.1 localhost
[COLOR="Blue"]**127.0.1.1 desktop.DougsBox**[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
doug@douglas-desktop:~$ 


```

Ok, drop on your terminal and issue the following commands below:

-Open the hosts file for editing:
```
gksudo gedit /etc/hosts
```

-Replace the value of (the colored Blue text on top):

**> 127.0.1.1 desktop.DougsBox**

to

**> 127.0.1.1 douglas-desktop**

Save and Close the file. While on your terminal, issue the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tropdoug on 2008-08-23
I think this might be part of the problem. 

I have been seeing this in the terminal 

```
doug@douglas-desktop:~$ sudo gedit /etc/fstab
[COLOR=Blue]sudo: unable to resolve host douglas-desktop[/COLOR]

```

and did not take much notice. But the output from the cat command shows 

```
[COLOR=Blue]127.0.1.1 desktop.DougsBox[/COLOR]

```

Maybe I named something wrong???

---

### Post by tropdoug on 2008-08-23
I was typing same time as you posted. This is what I got when I ran the first command


```
doug@douglas-desktop:~$ gksudo gedit /etc/hosts
No protocol specified

(gksudo:6579): Gtk-WARNING **: cannot open display: :0.0
doug@douglas-desktop:~$ 

```

---

### Post by iaculallad on 2008-08-23
> **tropdoug said:**
> I was typing same time as you posted. This is what I got when I ran the first command


```
doug@douglas-desktop:~$ gksudo gedit /etc/hosts
No protocol specified

(gksudo:6579): Gtk-WARNING **: cannot open display: :0.0
doug@douglas-desktop:~$ 

```

Try this on your terminal:

```
xhost +local:
```

then, redo the command I posted above to fix your hosts file.

---

### Post by tropdoug on 2008-08-23
doug@douglas-desktop:~$ xhost +local
No protocol specified
xhost:  unable to open display ":0.0"


same answer

---

### Post by iaculallad on 2008-08-23
> **tropdoug said:**
> doug@douglas-desktop:~$ xhost +local
No protocol specified
xhost:  unable to open display ":0.0"


same answer

Try to insert the **[COLOR="Blue"]:[/COLOR]** character:

```
xhost +local:
```

---

### Post by tropdoug on 2008-08-23
iaculallad

I think I broke it! 
I tried both colon and semi colon with results below. 

What I might do is start again, its not a big deal to reinstall and perhaps pay a little more attention this time. Unless you have any other ideas?

```
doug@douglas-desktop:~$ xhost +local:
No protocol specified
xhost:  unable to open display ":0.0"
doug@douglas-desktop:~$ xhost +local;
No protocol specified
xhost:  unable to open display ":0.0"
doug@douglas-desktop:~$ 

```

Doug

---

### Post by tropdoug on 2008-08-23
UPDATE

I decided that I had broke it! soI did a reinstall, man I have to say that the current install procedure from disc is an absolute dream, finds all my wireless stuff, printers and configures effortlessly. 

This time I carefully studied the partition possibilities, and reformatted sda2 and made it / and also added the /home mount point to sdb1

ten minutes later and all is well. The host issue is sorted, admin programs working well /home auto mounts, and the despktop and bookmarks are exactly as they were on 7.10 which is what I wanted and everything else, (as far as I can tell) is working like lightening. Fantastic. I am just doing the final apt-get upgrade and then off to bed. 

Thank you all for your help. 

Douglas

---

