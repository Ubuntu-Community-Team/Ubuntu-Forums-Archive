---
title: "Upgrade from 12.04 to 16.04 and libc does not perform rdns now?"
date: 2017-01-24
forum: Installation &amp; Upgrades
---

### Post by tech-j on 2017-01-24
I recently upgraded a machine from 12.04.5-LTS to 14.04, then to 16.04 to get it current.
Since then I have noticed that my scripts started failing.

So I started by checking the Auth Log and see this very ambiguous error:
server sshd[1356]: message repeated 2 times: [ userauth_hostbased mismatch: client sends another-server.domain.com, but we resolve 172.16.1.89 to 172.16.1.89]
server sshd[1418]: message repeated 2 times: [ userauth_hostbased mismatch: client sends alternate-server.domain.com, but we resolve 172.16.1.18 to 172.16.1.18]

So then I did a "last" to see if it was doing the RDNS, which it is not doing.
root     pts/0        172.16.1.96      Tue Jan 24 16:41   still logged in
root     pts/0        172.16.1.96      Tue Jan 24 16:28 - 16:41  (00:12)

But if I do a "last" on my 12.04.5-LTS Machine, it does show the server names instead of the IP's and it is not having the "Auth" Issues show above.
root     pts/12       admin.domain.com Sun Jan 22 22:01   still logged in   
root     pts/12       admin.domain.com Sat Jan 21 13:59 - 15:02  (01:03) 

If I run a "host" query from the command line, it properly resolves names to IP's and IP's back to names, no problem.
So I am trying to figure out how to get libc to do RDNS mapping again to prevent the Auth Failures based on DNS/IP Names when connecting via SSH.

What changed that this is not working now?
Has anyone else noticed this issue when upgrading?

Please advise.
Tech-J

---

### Post by tech-j on 2017-01-25
Update.
I have been running through other threads and have found the suggestion to make the change in /etc/gia.conf to force IPv4 checks only.
# For sites which prefer IPv4 connections change the line to:
precedence ::ffff:0:0/96  100

This still did not correct the issue. :(
I am at a loss as to why libc cannot seem to perform RDNS, which is preventing SSH from being able to do it.

I would appreciate any suggestions / guidance.
Tech-J

---

### Post by mörgæs on 2017-01-26
Libc is one of the central packages in a GNU/Linux distro and I would expect it to be in a neverending change. 


Are you able to test the scripts in a live boot of 16.04.1?

---

### Post by tech-j on 2017-01-26
Hello Morgaes.
Thank you for your question.
As I mentioned in my last post, it does not matter whether you do it from Live or from a clean install.

You can check this yourself on your machine by simply running the command "last" (or sudo last if you are not root).
You will see that it shows all the external SSH logins in IP format instead of the machine.domain.com format.
The scripts only fail because SSH tries to do a reverse map of the connection IP to the "announced" hostname of the connection.
Since SSH uses libc to do this, I am trying to figure out if this is a "Bug" that needs to be reported to Ubuntu, or if there is yet additional configuration that needs to be done now that they have switched to using OpenBSD SSH.
I am aware that I could disable DNS checks in SSH, but we require each of these connections to be logged, so we want it on, but we also need it to work.

Thanks.
-Tech-J

---

### Post by mörgæs on 2017-01-26
> **tech-j said:**
> As I mentioned in my last post, it does not matter whether you do it from Live or from a clean install.

I didn't see that mentioned but anyway, now we know. 


> **tech-j said:**
> 
You can check this yourself on your machine by simply running the command "last" (or sudo last if you are not root).
You will see that it shows all the external SSH logins in IP format instead of the machine.domain.com format.

I don't run a server with external access but if anyone does he/she can hopefully do the test.

---

### Post by tech-j on 2017-02-06
Hello Everyone.
I am still trying to find a resolution to this issue.
If there are any out there that have experienced this and have a solution, please let me know.

Thanks!
-Tech-J

---

