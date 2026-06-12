---
title: "INstalled Ubuntu 9.10 ok, but can't make DSL connection to work"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2009-12-26
I'm new to Linux.  I installed it partitioning the HD, (WXP remains in a 54GB partition, Ubuntu in a 20GB partition and the rest is free space).

I can connect by running the command in Terminal

sudo pppoeconf

answering Yes to everything, entering username and password when requested.

Bu I want it to be automatic, or at least I would like to run the batch file (or name it as it should be named).

I created the DSL connection in the newtork icon (above right), username, password (blank in Service, what should be entered here?). But it doesn't connect when I click on it. Worse, I was requested my password for authentication many times with success, as I am the administrator (I guess), but now, it request my password to edit the DSL connection but the authentication fails.

? ? ?

---

### Post by gordintoronto on 2009-12-26
Could you describe your setup?  If I were guessing, I would say you have a DSL modem which is connected by ethernet cable to an ethernet port on your computer.  Is that right?

Did your ISP supply the DSL modem?  Did they give you any instructions for it?  Normally, you set up the modem so that it automatically supplies the logon userid and password provided by the ISP.

When you run Ubuntu, you are NOT the administrator, but by suppling your Ubuntu password, you can do administrator tasks.

---

### Post by rva1945 on 2009-12-26
> **gordintoronto said:**
> Could you describe your setup?  If I were guessing, I would say you have a DSL modem which is connected by ethernet cable to an ethernet port on your computer.  Is that right?

Did your ISP supply the DSL modem?  Did they give you any instructions for it?  Normally, you set up the modem so that it automatically supplies the logon userid and password provided by the ISP.

When you run Ubuntu, you are NOT the administrator, but by suppling your Ubuntu password, you can do administrator tasks.


Only God knows why I can now automatically connect to the Internet. Maybe I allowd modem usage and connection to the Internet privileges to my user...

BY the way: how can I set Windows XP as the default boot selection (it's for my wife, still in the process of being convinced), and more that 7 seconds of time?

---

### Post by gordintoronto on 2009-12-26
> **rva1945 said:**
> Only God knows why I can now automatically connect to the Internet. Maybe I allowd modem usage and connection to the Internet privileges to my user...

BY the way: how can I set Windows XP as the default boot selection (it's for my wife, still in the process of being convinced), and more that 7 seconds of time?

If you are connected to a router by ethernet cable, you should have immediate access to the Internet, even from a live CD.

I don't know enough about Grub to answer your by-the-way.  Please start a new thread, with the subject, "Grub question."

---

### Post by SuperEngineer on 2009-12-28
although the wrong forum... the answer re your Grub btw  [assuming you've installed Ubuntu 9.10] is install 'Startup Manager'...  a quick, easy & safe way to select default boot and timeout]

Cheers.

---

