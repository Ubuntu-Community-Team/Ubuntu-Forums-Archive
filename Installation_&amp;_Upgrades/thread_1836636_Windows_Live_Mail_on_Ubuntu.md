---
title: "Windows Live Mail on Ubuntu"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by be0562 on 2011-08-31
Hi everyone,

1st post, so apologies for any mistakes..

I have just switched from Vista to Ubuntu. I can't stand Microsoft so don't intend to dual boot and so am trying to set everything up to have the same functionality as before.

I use multiple hotmail accounts which I have read about are all pop3 for email clients. Windows live mail apparently does something clever to access them and all the correct folders, which I haven't been able to replicate with evolution/thunderbird.

What I want is a mail client to:
Open a hotmail account, sync emails in all folders shown in hotmail (webmail), i.e. inbox, outbox, sent items, drafts....
Leave emails on the server, only deleting if I manually delete.
Load all previous emails from all folders shown on the mail server.
Do this for all multiple accounts, yet remain separated from each other.

Evolution and Thunderbird are failing in 1 or more of the above.

I have installed Wine, but not been able to get the windows live mail standalone installer to work, and not found instructions on the net.

So either I need a badass email client, or I need to run windows live mail. Can anyone out there help me please???


I am new to Ubuntu, confident I can follow terminal commands, however I'm still finding my way around linux. Now off to the beginner thread to find out some basics..

Thanks

---

### Post by YesWeCan on 2011-09-01
What is Thunderbird failing to do?

---

### Post by Mark Phelps on 2011-09-01
According to the WineHQ application compatibility rating for Windows Live Mail -- you are out of luck.  Garbage means it's not going to work  -- no matter what you do:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7436]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=7436")

---

### Post by davidm2232 on 2011-09-01
> **YesWeCan said:**
> What is Thunderbird failing to do?
Thunderbird does not seamlessly synchronize hotmail folders. Ie If i move a message to my "archive folder" it is moved both on the local client and on the webmail interface.

---

### Post by aura7 on 2011-09-01
I have not tried with Evolution with hotmail account, if someone has tried can he share his experience with evolution regarding hotmail accounts and its syncing.

---

### Post by sunfromhere on 2011-09-01
> **be0562 said:**
> Hi everyone,

What I want is a mail client to:
Open a hotmail account, sync emails in all folders shown in hotmail (webmail), i.e. inbox, outbox, sent items, drafts....
Leave emails on the server, only deleting if I manually delete.
Load all previous emails from all folders shown on the mail server.
Do this for all multiple accounts, yet remain separated from each other.


Thanks

Hello, I've done the Hotmail-Thunderbird thing, and I'm not experiencing any problems. Only my junk mail isn't synced, but I don't find it necessary.

First, when you added your Hotmail account to Thunderbird, visit Hotmail in your web browser. It will ask about "another programme accessing mail" or something simmilar. Or - you can find it later in clicking on your name - options - mail options. This gives you: 

**[SIZE=2]"POP and deleting downloaded messages[/SIZE]**

         [SIZE=2]             If you use POP to download Hotmail messages to another  program, that program could make it so you can't read your messages on  Hotmail. (For example, this might happen if you use Mac Mail or Mozilla  Thunderbird).         [/SIZE]
         [SIZE=2]
[/SIZE]                                                  [SIZE=2]a) Don't  let another program delete messages from Hotmail. (If your other  program is set to "delete messages from the server," we'll simply move  them to a special POP folder. They won't be deleted.)[/SIZE]             
                                                  [SIZE=2]b) Do what my other program says-if it says to delete messages, then delete them.[/SIZE]"


Sent messages, drafts, etc you configure in Thunderbird's options for the said account (Edit-Settings-Copies and Folders)
On first run, Thunderbird automatically fetched all my mail in the inbox, and keeps fetching them even if I've already read it in the browser. 

To be noted is that I'm running Thunderbird 6.0.1, not the one found in the Ubuntu Software Repository; don't know if it makes a difference.

Hope I helped a bit.

addition: Check your Thunderbird's Server settings (Edit-Settings-Server Settings) for mail downloads, deletion and leaving them on server.

---

### Post by The Llama on 2011-09-01
I don't think Hotmail support IMAP, this is a tactical decision to ensure that people with a Hotmail account who want to sync their e-mails have to use Windows Mail: The only mail application that will sync Pop Hotmail messages to the web.
My recommendation: Switch to another e-mail provider that allows IMAP, i.e. Gmail, GMX, Mail.com, Yahoo, AOL ext.
If you'd like to keep your Hotmail account you could set it up on Thunderbird with POP then create a message filter to copy (or move) all incoming messages to a folder on another account that does use IMAP: Yahoo for example. This way, you can access your messages on mail.yahoo.com even though you still maintain a Hotmail address.

---

### Post by be0562 on 2011-10-05
Hi all,

Thanks for your replies. It seems that I would have to set up filters for thunderbird, but then all my mail in hotmail would be in one pop folder. (If I was logging into my emails away from my laptop I would have to use hotmail, so wouldn't want this.)

I have found the options to remotely delete the messages and hotmail luckily realises when this is happening and gives you an option before deleting anything.

So it seems yet again, microsoft has managed to annoy me yet again. I will consider changing my email away from hotmail, but for now I am using webmail and have linked all the accounts, so I only need to type in one password to access all of them.

For now my questions are answered so I'll close the thread thanks once again.

---

