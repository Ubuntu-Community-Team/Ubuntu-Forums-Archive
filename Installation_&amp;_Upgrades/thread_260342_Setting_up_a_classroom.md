---
title: "Setting up a classroom"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Chado on 2006-09-18
Hey.
I've been given a project at my high school. I am to set up my programming lab with Linux and it is to have logins so that users can access their specific folder. Haven been a long time Kubuntu user and no one else in the room that knows Linux, we're going with Kubuntu. What I need to know is how to set up it up so that when a student sits down at the computer, he or she can punch in a name and password and it will give him or her access to his or her files only. All other programs will be installed on the machines, but this student needs to be able to save his or her files on this machine only. I don't want to pull programs from the machine. I'm working with Dell Opti something Gn+1 400MHz machines. So it's nothing fancy or complex. Fell free to ask questions or leave suggestions.
Thanks
Chado

---

### Post by orb9220 on 2006-09-18
[http://www.ubuntuforums.org/showthread.php?t=201023&highlight=thin+clients](http://www.ubuntuforums.org/showthread.php?t=201023&highlight=thin+clients)
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=thin+client](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=thin+client)

---

### Post by ximok on 2006-09-18
Need more information:
A. How are you managing usernames and passwords? (Passwd/shadow? Active Directory? Ldap? NIS?)

B. What kinds of directories are we talking about?
B.1. Will the student be assigned a computer and just have to use the local account on the same computer every day? (Problem solved, student uses the same computer every day and automatically has access to their home directory on THAT machine)

B.2. Are the directories on a server and each student will possibly be on a new machine each day?

B.2.1. What kind of file server are we talking about? (Windows Server, Samba, NFS?)

Need more info about your network!!!

---

