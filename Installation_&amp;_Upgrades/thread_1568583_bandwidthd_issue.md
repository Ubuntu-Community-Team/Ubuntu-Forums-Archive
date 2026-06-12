---
title: "bandwidthd issue"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by nbhuwania on 2010-09-05
I am unable to install bandwidthd either from software resource or from update manager.....this is also resulting in non installation of gnucash....

please help

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by ganesh_thevar on 2010-09-21
This is one of the issues that troubles those are new to Ubuntu. I had also faced the same problem and after one month of searching I finally found the solution in an forum archive - [http://ubuntuforums.org/showthread.php?t=553918](http://ubuntuforums.org/showthread.php?t=553918). 

I am reproducing the set of instructions from the archive for your benefit. 

Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the  broken package, remove the info for that package. Here search bandwidthd  package and then remove all details under it.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

[COLOR=Red]Points to remember[/COLOR]
Before getting on to step 1 ensure that you login as a root. Only then will you be able to edit the said file. The file could be located from the File System (Places/Computer). After opening the file search for bandwidthd and just select the  content related to it and delete it. Step 2 onwards are to be performed on the terminal (Applications/Accessories)  also as root user. Step 4  is actually two sets of commands that has to be performed separately i.e.,  * apt-get update* and then* apt-get -f install*. When I followed Step 5 I got a error message. So I improvised and repeated Step 2 which appears similar. Step 6 and 7 are to be followed as it is. 

Once all the instructions are followed. logout as root and login as your username. You will know if this has worked for you when are able to install packages which earlier you had encountered problem with. 

[SIZE=3]Most important[/SIZE] forget bandwidthd once and for all. Let it rest in peace. It will not bother you till you try to install it again. Trying to reinstall it again will result in you facing  the same problem again.  

:smile: Enjoy Ubuntu

---

