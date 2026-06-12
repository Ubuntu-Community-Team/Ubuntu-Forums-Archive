---
title: "Trying to locate email files on server"
date: 2016-09-06
forum: Installation &amp; Upgrades
---

### Post by Robert_Boutin on 2016-09-06
I recently completed a LAMP server setup on 16.04 Server using the PerfectServer guide.  Everything now seems to be working well but I'm struggling with an email issue.  I want to convert downloaded eml files from my prior third-party email provider and transfer them onto the server in the correct location.  However, for the life of me I can't locate where on the server my email files are being stored.  Can anyone help me out with some guidance?  Thanks

---

### Post by TheFu on 2016-09-07
Use an email client connected to both systems and drag-n-drop messages over using the EMAIL CLIENT.  Email servers don't normally use EML files, so those aren't really useful.

---

### Post by SeijiSensei on 2016-09-07
It might be possible to convert the eml files back into an "mbox" mail folder like this:
```

cd /path/to/emls
touch mailbox
for f in *.eml
do
     cat $f >> mailbox
     echo "" >> mailbox
done

```
That  should create a valid mbox folder containing each message delimited by a blank line.  Then you can try copying "mailbox" to /var/mail/yourusername on the server
```

sudo cp mailbox /var/mail/yourusername
sudo chown yourusername:yourusername /var/mail/yourusername
sudo chmod 600 /var/mail/yourusername

```

If you connect with an IMAP client, the messages should appear as your inbox.

If you create the directory /home/yourusername/mail/ on the server and copy "mailbox" into that instead, then the messages will be part of your folder tree.  You may need to "subscribe" to "mailbox" with your IMAP client to see it.  Make sure this mail/ directory and its contents are all owned by yourusername.

I recommend installing the [SIZE=3]alpine[/SIZE] text-only mail client on the server.  It's incredibly useful when you're trying to administer e-mail accounts.  You can access the folders with IMAP or directly through the filesystem like /home/myusername/Sent.  You can also exercise your root powers and manage other people's mailboxes using the su command.

---

### Post by Robert_Boutin on 2016-09-08
Thanks to both of you for the advice. Unfortunately I just did something stupid that demonstrates why I shouldn't be doing this myself.  I basically had to completely reconstruct my server because I hadn't backed anything up before trying (and miserably failing) to install NextCloud.  So at the moment this particular issue is the least of my concerns, more important is to get back to its previous state... It will probably be the weekend before getting back to this.

---

### Post by TheFu on 2016-09-08
IMHO, email is dangerous enough to be on a server install all-by-itself.  Use VMs for this separation. Any internet facing service should be compartmentalized and dangerous services like web and email and dns should get extra protection of a reverse proxy to make it THAT much harder for crackers to get into the real systems.

Also, daily, automatic, versioned, backups are the first thing to be setup on any server. Think of all the things that could go wrong - backups make those 1,000 things an inconvenience, not a total loss.

---

### Post by Robert_Boutin on 2016-09-08
> **TheFu said:**
> IMHO, email is dangerous enough to be on a server install all-by-itself.  Use VMs for this separation. Any internet facing service should be compartmentalized and dangerous services like web and email and dns should get extra protection of a reverse proxy to make it THAT much harder for crackers to get into the real systems.

Also, daily, automatic, versioned, backups are the first thing to be setup on any server. Think of all the things that could go wrong - backups make those 1,000 things an inconvenience, not a total loss.

Thanks, your advice is noted.  I honestly want to cry right now, it really was working absolutely perfectly.  Lesson learned...  the very hard way.

---

### Post by Robert_Boutin on 2016-09-10
All I can say is wow, I wish I had received this advice a lot sooner.  I did a fresh install of 16.04 Desktop on my server and installed Virtualbox.  Now I have three virtual servers running and whenever I do something I regret, it's simply a matter of going to the basement to restore a snapshot. And as I make progress I'm happy with, I take a snapshot.  Jeez have I wasted so much time starting over and over and over...  TheFu is the bomb, thanks for your help, I've saved so many hours already.

---

### Post by TheFu on 2016-09-10
Vbox is a toy compared to other options.  I've seen it lock up a hostOS AND all VMs - BRS required.  I've never seen KVM do that - not once in 6+ yrs using it in production. If you want servers running 24/7/365/10, use something other than vbox.          Just sayin'.

BTW, your setups could be automated too. [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
I get lots of reuse from my ansible playbooks.  Wanted to setup a 16.04 server to test something out yesterday - took 35 min with only 15 min that I had to watch.

---

