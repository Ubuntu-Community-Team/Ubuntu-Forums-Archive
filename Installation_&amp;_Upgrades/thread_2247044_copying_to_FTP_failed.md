---
title: "copying to FTP failed"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by Jassim_Rahma on 2014-10-05
Hi,


I am trying to copy a CDR file from cisco CDR to my vsftpd but I am getting this error on the Cisco PBX:


[http://kb.globalscape.com/Knowledgeb...icle10303.aspx](http://kb.globalscape.com/Knowledgeb...icle10303.aspx)




can anyone help on how to solve this please?


Note: Cisco PBX doesn't allow to change the file name because it's automatically generated.

---

### Post by nerdtron on 2014-10-05
Hmm your link is broken?

---

### Post by Jassim_Rahma on 2014-10-05
[http://kb.globalscape.com/KnowledgebaseArticle10303.aspx](http://kb.globalscape.com/KnowledgebaseArticle10303.aspx)

---

### Post by nerdtron on 2014-10-05
May we know your exact command when you upload?

---

### Post by Jassim_Rahma on 2014-10-05
it's in the cisco PBX and it's configured by Cisco partner here.

The upload is working when I upload to my laptop (which has Filezilla FTP server) but failed when changing the ftp server address to linux

---

### Post by nerdtron on 2014-10-05
Do you have access to the vsftp server? What folder will the file be saved? What is the permissions of this folder?

---

### Post by Jassim_Rahma on 2014-10-05
the flder is called cdr and there is a write permission. I have no problem uploading any file to the folder using the ftp client.

The problems occurs when cisco copies its files..

by the way, I forgot to mention the cisco file name is something like this:

> [COLOR=#333333][FONT=Lucida Grande]cdr.IPPABX.07_23_2014_11_41_23.384[/FONT][/COLOR]

---

### Post by nerdtron on 2014-10-06
> I have no problem uploading any file to the folder using the ftp client.

So you provided username/password when you upload? Does the cisco have the same credentials?

---

### Post by Jassim_Rahma on 2014-10-06
the problem is not with cisco for sure. I tried Filzilla client when uploading a file to the vsftpd. I can upload any file but when I upload a file with the mentioned name it will fail.

---

