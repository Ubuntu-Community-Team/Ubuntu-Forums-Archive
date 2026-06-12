---
title: "^m"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by mrkazino on 2008-02-19
I have the classic ^M end of line issue when I promote files from a Windows development environment to my 6.10 server running Apache2 and Tomcat. There are many files that are promoted every few days so having to constantly sed or perl them is a pain. 

To determine if the issue is on the Ubuntu or Windows dev server, I connected a second Windows development server to the Ubuntu server and  imported a complete website where the files were known to have the ^M issue.
I then promoted these files to a Redhat server's web folder and  none of the files had the ^M issue.
I then promoted a website from the  second Windows development environment that was on the Redhat server to the Ubuntu server. The files all had the ^M at end of line.

Both Windows development environments are XP running an Eclipse development environment using sftp to import/export the files.

Both the Redhat and Ubuntu locales are UTF-8

I should also say that I use Sun Jave Studio Creator and that the jsp's and xml files in my war files once exploded also contain the dreaded ^M. But again only when I promote them to this Ubuntu server. For html and php projects I use EasyEclipse for PHP. 

There must be something I've done in the setup of the Ubuntu server this time as I don't believe I had this issue before I upgraded to 6.1

Any ideas would be greatly appreciated !

---

