---
title: "FTP repository"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Aliby on 2008-04-30
Where has the FTP protocol option gone to in Synaptic?
In Gutsy I could select the repository I wanted and then choose the FTP protocol below that. Now it just gives me the option of HTTP?
If I edit the sources list to change the HTTP to FTP it works OK, but the Repositories in Synaptic think they are now 3rd party sources.

Have I done something wrong or is it a bug?
:confused:

---

### Post by dsiembab on 2008-04-30
did you change gutsy to hardy in the url?

---

### Post by Aliby on 2008-04-30
I'm not in Gutsy anymore .. I did not upgrade.
I am in a new installation of Hardy.

I open Synaptic and menu select: "Settings"-"Repositories"

On the first TAB it gives you the "Ubuntu Software" options.
About halfway down there is a drop down list titled:
**Download from:** and in Gutsy I got mine to read:
**[ftp://ubuntu.mirror.ac.za/ubuntu-archive](ftp://ubuntu.mirror.ac.za/ubuntu-archive)**

This was achieved with the drop down and choosing **Other..**
Under South Africa ... **ubuntu.mirror.ac.za**

The below that there is a **Protocal:** option where I selected: **ftp**

It Hardy the only Protocol there is HTTP. If I edit the sources.list to point to the ftp Synaptic no longer sees it as "official" and ommitts it from the "Ubuntu Software" TAB and unchecked all the options there. All the lists are now shown under the "Third Party" TAB.

It works fine, but it's just a bit messy if I want to add or uncheck an option it don't work ... I need to edit the file again.

---

### Post by dsiembab on 2008-04-30
I thought the repositories had labeling protocol in files system like [http://repository/gutsy/](http://repository/gutsy/) blah blah blah
That's what I meant. You know like if you wanted to change your repository to would change gutsy to hardy.  even with ftp. id you think of using [ftp://ubuntu.mirror.ac.za/ubuntu-archive/dists/hardy](ftp://ubuntu.mirror.ac.za/ubuntu-archive/dists/hardy) does this make any sense. Follow your own link that you posted 
you could even use [ftp://ubuntu.mirror.ac.za/ubuntu-archive/ubuntu/dists/hardy](ftp://ubuntu.mirror.ac.za/ubuntu-archive/ubuntu/dists/hardy)

---

### Post by Aliby on 2008-05-27
Can anyone tell me where I find the system file that has a list of the "current" repository mirrors for Ubuntu?

I'm not talking about the sources.list file. 
The Synaptic Options tab must be getting the mirrors list from somewhere for you to select. Once selected Synaptic updates the sources.list with your selection.

I expect that it is a separate file that provides the options in Synaptic. If it is a text file then all I need to do then is to add the FTP protocol in that file for the mirror I use ...
:confused:

---

### Post by dsiembab on 2008-05-27
What is so great about this ftp site anyways?

---

### Post by Aliby on 2008-05-28
I do seem  little pedantic hey?
:lolflag:

FTP sites are usually a lot faster and, more importantly for me, are not usually subject to a Proxy. This means for example that I can run Ubuntu at work and still access updates and new installs etc.

:)

---

### Post by dsiembab on 2008-05-28
yeah:)
On the speed part couldn't you just choose best server in your repositories connection, i find this helps on finding the fastest connection for my synaptic. Well if the sight you are used is a trusted source then I don't think it would matter if it comes up as third party as long as it's a trusted source.

I found this maybe it will help copy paste this into your browser ```
file:///usr/share/synaptic/html/index.html
``` might help out

---

### Post by vgrisham on 2008-06-15
> **dsiembab said:**
> yeah:)
On the speed part couldn't you just choose best server in your repositories connection, i find this helps on finding the fastest connection for my synaptic. Well if the sight you are used is a trusted source then I don't think it would matter if it comes up as third party as long as it's a trusted source.

I found this maybe it will help copy paste this into your browser ```
file:///usr/share/synaptic/html/index.html
``` might help out

It's not a matter of trusted sites. I connect through my local university wirelessly and they block http protocol via their proxy server. This is quite common in corporate networks, and we need to have the option to update via FTP again.

---

