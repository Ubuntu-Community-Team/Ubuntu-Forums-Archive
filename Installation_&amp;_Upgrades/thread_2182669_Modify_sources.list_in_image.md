---
title: "Modify sources.list in image"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by TheFuzz4 on 2013-10-22
Hey Everyone,

So I finally got my PXE boot working.  Now what I would like to do is to modify the sources.list file that is included with the installer to point to my local mirror instead of the Ubuntu ones.  Nothing against them its just faster to pull locally :).  Can anyone help point me in the right direction for this?  Thanks.

---

### Post by Lars Noodén on 2013-10-22
The local ones are more appropriate, not just faster.  The data will travel a shorter distance and thus reduce the traffic jam.  You're not *in* a traffic jam, you *are* the traffic jam. ;)

Anyway, you can try generating a sources.list file using this web page:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

The result can be pasted into your file.

---

### Post by TheFuzz4 on 2013-10-22
Where does the file go in the installer?

---

### Post by Lars Noodén on 2013-10-22
If you're working with the GUI it would go something like this:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Or you could work through the shell in the terminal.

```

sudo nano -w /etc/apt/sources.list
sudo apt-get update

```

---

### Post by TheFuzz4 on 2013-10-22
:) I mean on my server that hosts my PXE installs.  I have copied the contents of various Ubuntu iso (myth, server, desktop, gnome) and setup the PXE boot.  But I want to give the PXE installs a new sources.list so that during the install process they don't hit the ubuntu mirrors and instead hit mine.

---

### Post by Lars Noodén on 2013-10-22
That's harder.  I happen to still have PXE set up on one machine but it is quite out of date, one being for natty and the other for precise.    I don't see any place to set repositories.  

The hard way might be to rework the netboot image to have the defaults you want.  

Another choice might be to add preseed or kickstart to your PXE kernel's boot options and have them point to a file with the right options.

Of those, I'd try setting kickstart or preseed.  I used to have kickstart set up to customize apps and the repositories.  I found kickstart easier to work with but less reliable.  preseed seems to be the way to go except for (what I perceive to be) the lack of documentation.  Watch out though, errors will produce no warning messages and simply fail silently making it hard to figure out what went wrong.

---

