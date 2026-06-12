---
title: "Differences in install methods (Server/Desktop/Alternate)"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by tufkal on 2008-04-25
I am curious just what is the difference between server and desktop installs?  They use the same repos, and same kernel right?  You could get up and running with one and have it identical to the other after some package management right?  Then why is one supported longer than the other?  And what about the command line install option?  Doesnt that just install the server version?  

*Head Explodes*

Can someone fill in the blanks here?

Desktop CD Install =
Desktop CD Install (Command Line Option) = 
Server CD Install =
Server CD Install (Command Line Option) =
Alternate CD Install =
Alternate CD Install (Command Line Option) =

It seems to me there is some overlap here, or I really dont understand the command line option, or I really dont understand the server release, or I need more brandy.

Can someone help me out here?  I want to setup Hardy and I want to get the right CD from the start for what I need.

---

### Post by tufkal on 2008-04-25
Like for example...
Desktop CD Install = Desktop
Desktop CD Install (Command Line Option) = Server
Server CD Install = Server
Server CD Install (Command Line Option) = Server 
Alternate CD Install = Desktop
Alternate CD Install (Command Line Option) = Server

That would make no sense to me, but could be right....

Can someone help me understand this?

---

### Post by nick09 on 2008-04-25
The server edition is just made for servers which host websites(such as this one).

---

### Post by tufkal on 2008-04-25
> **nick09 said:**
> The server edition is just made for servers which host websites(such as this one).

So the server edition's default package set has apache in it....

That doesn't help... :(

Anyone else who has more experience?

---

### Post by martrn on 2008-04-25
> **tufkal said:**
> I am curious just what is the difference between server and desktop installs?  They use the same repos, and same kernel right?  You could get up and running with one and have it identical to the other after some package management right?  Then why is one supported longer than the other?  And what about the command line install option?  Doesn't that just install the server version?  

*Head Explodes*

Can someone fill in the blanks here?

Desktop CD Install =
Desktop CD Install (Command Line Option) = 
Server CD Install =
Server CD Install (Command Line Option) =
Alternate CD Install =
Alternate CD Install (Command Line Option) =

It seems to me there is some overlap here, or I really don't understand the command line option, or I really don't understand the server release, or I need more brandy.

Can someone help me out here?  I want to setup Hardy and I want to get the right CD from the start for what I need.

The Desktop CD Install installs from within a nice graphical interface, and I believe previously had no repository on the CD, it just copies the files across from the cd and eats up memory because it is running a live version as it installs.  Excellent if you do not want to install via a menu driven intreface or a command line system.

The Alternative CD installs in a command line environment or menu driven interface, is easy to customize as you go along if you know what you are doing, making it easy to install on low system requirement and does not cause many of the failed installations as the Desktop CD.  The alternative CD has a repository on the CD.

The Server CD does not install any desktop environment, such as kde or gnome, and installs a kernel that is less responsive to user inputs (via mouse or keyboard) and is more responsive to disk activity. IE it installs a slightly different kernel.  With a server cd if you want a desktop you have to install it via the repositories by apt-get install ubuntu-desktop. The server cd has repository sources on the CD.

That I think are the main diffrences.

---

### Post by tufkal on 2008-04-25
> **martrn said:**
> The Desktop CD Install installs from within a nice graphical interface, and I believe previously had no repository on the CD, it just copies the files across from the cd and eats up memory because it is running a live version as it installs.  Excellent if you do not want to install via a menu driven intreface or a command line system.

The Alternative CD installs in a command line environment or menu driven interface, is easy to customize as you go along if you know what you are doing, making it easy to install on low system requirement and does not cause many of the failed installations as the Desktop CD.  The alternative CD has a repository on the CD.

The Server CD does not install any desktop environment, such as kde or gnome, and installs a kernel that is less responsive to user inputs (via mouse or keyboard) and is more responsive to disk activity. IE it installs a slightly different kernel.  With a server cd if you want a desktop you have to install it via the repositories by apt-get install ubuntu-desktop. The server cd has repository sources on the CD.

That I think are the main diffrences.

That is what I was looking for.  Thank you!

Desktop CD = Live Install GUI 
Alternate = Customizable GUI or Command Line
Server = Same as desktop but special set of packages installed for servers.

---

