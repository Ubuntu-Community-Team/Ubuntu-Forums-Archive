---
title: "Installation of Ubuntu 10.10 via PXE and Alternate CD"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by gmjs on 2010-10-20
Hello,

I'm having trouble getting Ubuntu 10.10 installed via PXE with a copy of the alternate CD.

Past versions I have tried have allowed me to copy the contents of the CD to a web server and then create a kickseed file to specify the 'mirror' as being on that web server.

As of 10.10 (and perhaps 10.04--I haven't tried it) the installer uses the United Kingdom mirror (which I assume is selected due to setting the required language) and disregards the url --url http:// line in the kickseed file.

The log produced doesn't even suggest that the local web server was checked--it tried [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) first.  As this server will hopefully install copies of Ubuntu without an Internet connection, the Ubuntu server will be unavailable.

Is there a change to the way the Debian installer works in this version?  Has anyone managed to use a web server to install Ubuntu 10.10 like this?

If not, I may have to switch to creating an NFS share instead.

Many thanks for any help,

Graham

---

### Post by gmjs on 2010-10-21
Hello,

Just in case anyone else finds this problem, I've been able to fix it by adding some lines to the preseed file.

I've added lines to tell the debian-installer where the mirror is too, but it appears that the important line is the one that states we want to use a custom mirror, rather than the default one for the selected country:

[HTML]d-i     mirror/country       string  manual[/HTML]


Sorry for answering my own post.  Hope it helps someone!

Thanks.

---

### Post by skmah on 2010-11-17
Hello gmjs,

I'm having the exact same problem. It looks like you solved it.

I've been using the same preseed file since Ubuntu 7.04. Now, it's trying to hit gb.archive.ubuntu.com even though I'm using an internal mirror (Ubuntu 10.10 alternate extracted and shared through http)

I tried:
d-i     mirror/country       string  manual

but still doesn't seem to work. 
I tried place the line before and after these lines:
d-i     mirror/http/hostname    string {my inter server}
d-i     mirror/http/directory   string /ubuntu/1010-64
d-i     mirror/suite            string maverick

Can you share your preseed file?

thanks
steve

---

### Post by skmah on 2010-11-18
It was a typo. My issue is solved. Thanks for pointing me in the right direction!

I had a double entry for mirror/country

The 2nd entry was wrong:
d-i	mirror/country	string	enter information manually

---

