---
title: "Java j2sdk-1_4_2-doc I can't install anything"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by Harryabreu on 2006-12-11
Hi, I have problems for install anything on Ubuntu 6.10 I found the packge j2sdk-1_4_2-doc.zip but I don't Know how I use it...could you helpme?
down you can read the message

Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
warning: file `/usr/share/doc/j2sdk1.4-doc/1.4.2/index.html' does not exist at /usr/sbin/install-docs line 821, </usr/share/doc-base/j2sdk1.4-doc> line 11.
warning: file mask `/usr/share/doc/j2sdk1.4-doc/1.4.2/*/*.html' does not match any files at /usr/sbin/install-docs line 826, </usr/share/doc-base/j2sdk1.4-doc> line 11.
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


My English is basic sorry my mistakes.

---

### Post by Gogol on 2007-05-10
ye, I have the same problem. I reinstalled java.. but i don't know what to do now.

I have Kubuntu and thanks to this gcc can't be installed.

Can anyone help me?

Thanks.

---

### Post by arsetonoseboy on 2007-06-29
What you are going to need to do is find those files which it is looking for:

j2sdk-1_4_2-doc.zip

j2sdk-1_4_2-doc-ja.zip

j2sdk-1_4_0-doc.zip

Download them and put them into your  /tmp directory inside the file system.
This will eliminate the update packager and synaptics from bugging you about them.
What is happening is that it's looking for the documents to add into the directory when it's trying to install JSDK. Much like windows when a file is not found, it can't complete the process of installing what you are trying to install. Only be it a major blessing, Linux and Ubuntu usually tells you what files are missing and sometimes where to find them. 

I may be a Ubunewb but honestly once I get help on how to get PC games to run on here 100%.. I'll be 100% sold on Ubuntu and Linux. I'm at 85% atm.. 

Till next time
Arsetonoseboy Out.:)

---

