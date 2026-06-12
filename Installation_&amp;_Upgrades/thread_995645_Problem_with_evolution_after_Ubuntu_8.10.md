---
title: "Problem with evolution after Ubuntu 8.10"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by maatta on 2008-11-28
I had Ubuntu 8.04 in my old computer. I turned that into home server preserving the old home-directory. I installed Ubuntu 8.10 to my new computer and mounted the old /home-directory to be used in this new Ubuntu 8.10 installation. I first tried Evolution and there seems to be problem with that. 

When I opened it, there was a notification that Evolution will change the format of mailboxes. This took some time - about 15 minutes. After that Evolution opened and started to load e-mails from ISP's POP3 server. However, it did not go well at all. In the bottom of main window, Evolution informs the tasks that are under progress. It seems that everytime it gets a new mail from the server, it wants to save a folder (I guess it saves the Inbox folder). I have 100 Mb/s network and this saving takes more than 5 minutes. If I look at the network traffic it seems that there is a lot of traffic from NAS to desktop computer. I am wondering what that is, if Evolution should be saving a folder.

I watched that about half an hour last night and then I went to bed. This morning I checked the situation and there has been some progress. Evolution had downloaded about 10 messages, BUT it had copied each 6 times. Also there were about 20 messages in the server that had not been downloaded at all. I know this because I can access the server via web mail.

Is there a compatibility issue between old and new Evolution that is causing these huge data transfers? Why Evolution made several copies of downloaded messages to my Inbox? Is there a way to get this working, or should I move the old .evolution folder and start from the scratch? I still want to preserve my old mail and other stuff that is in the .evolution directory.

---

### Post by awam66 on 2008-11-28
The better way to keep your old settings would be to file>backup your setting on the old evolution first. Then use file>restore in the new one. I have a memory stick which I use for this purpose.

---

### Post by maatta on 2008-11-29
Thanks for you answer. I'll keep that in mind in the future. However, since I already have used new Evolution, which changed the folder structure, I cannot do that any more. :(

---

