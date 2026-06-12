---
title: "Unable to resolve hostname problem in Intrepid"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Coreo on 2008-10-16
I've been having the problem where every time I try to run a sudo command in terminal, it gives me the error of "unable to resolve hostname"

I've read through all the forums, and I understand how to fix it.
[http://ubuntuforums.org/showthread.php?t=770801]("http://ubuntuforums.org/showthread.php?t=770801")
This one covers the problem pretty much perfectly...

But there's one problem...

I have no "/etc/hosts" file. 
I do have a /hostname file, but it doesn't appear anything like the others I have been seeing in the fixes that I've found.

Also, Administration -> Network does not exist. There's Network Tools, but it doesn't let you change anything.
Is this lack of "Network" just in Intrepid?

Any help would be greatly appreciated!

---

### Post by Coreo on 2008-10-16
Also, from what I've read, the inability for Ubuntu to "resolve hostname" or resolve the localhost, could be the cause of occasional lock-ups that I've been getting.

Hopefully this problem can be fixed....it seems to be the root of a lot of problems.

---

### Post by Rocket2DMn on 2008-10-16
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by cariboo on 2008-10-16
If you are absolutely sure you don't have an /etc/hosts file. Restart in Recovery mode, when you get to the menu select drop to a root prompt. At the prompt type:

```
touch /etc/hosts
```

Next type:

```
nano /etc/hosts
```

add the following to the file:

```
127.0.0.1	localhost
127.0.1.1	<yourcomputername>
```

Where <yourcomputername> = the hostname of your computer.
Press Ctrl-o to save and Ctrl-x to exit.

If you aren't sure of your computer's name at the prompt type:

```
hostname
```

When you are finished type at the prompt:

```
reboot
```

Jim

---

### Post by Coreo on 2008-10-17
Quite sure I don't have a /etc/hosts

Unless I'm thinking of the wrong thing...
I have:
host.conf
hostname
hosts.allow
hosts.deny

I'll try out your suggestion and see if it works once I get home this evening.


Thanks a lot!


EDIT:   /etc/hostname contains the name of my computer...but doesn't have the local address part. I'll still need a /hosts file, right?

---

### Post by inportb on 2008-10-17
Yes, you need a hosts file.

---

### Post by Gina on 2008-10-17
To restore the Network menu item type
**sudo apt-get install gnome-network-admin** in a terminal.  This is a known bug - I thought it had been fixed but maybe not.

The "Unable to resolve host..." problem I've had a few times.  It seemed to derive from setting up a domain/workgroup for a LAN, adding .*domainname* to the computer name.  Removing that in **Hosts** tab in **Network** dialog fixed it.

---

### Post by plun on 2008-10-17
Gina.. Can you please file a bug ?  :)

(Mine was rejected when I couldn't point out exact package.)

---

### Post by Coreo on 2008-10-17
Ahhhhhh!!

There we go, that fixed it.
I knew it was missing something to do with networking...
I noticed that once I switched from Hardy, I no longer had the tool to change my location once I was at my parents house.
(I need to manually set up my connection at my parents house in order to use internet connection sharing)


Thanks a lot for the fix!

The Network menu method works just as well as the other, and also made me notice something else...
The Domain Name was set to "sympatico.ca", and it was also set as a Search Domain.
Perhaps this was a contributor to the problem.

Thanks again!

---

