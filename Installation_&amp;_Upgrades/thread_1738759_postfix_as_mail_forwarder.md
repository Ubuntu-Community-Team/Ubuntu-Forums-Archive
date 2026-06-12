---
title: "postfix as mail forwarder"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by vralfy on 2011-04-25
Hi,

i'm trying to configure postfix as virtual mailforwarder. I have a little server at home and i want my mailclients to send a mail (wich may contain a large attachment) to this little server an not to my provider. The server has to archive this mail and send it to the provider (as the mailclients should use to do [red lines]).

For example (blue lines)

I'm using thunderbird and I'm sending a mail as user@littleserver. The littleserver archives the mail an send it via googlemail as [EMAIL="mailnewb@googlemail.com"]mailnewb@googlemail.com[/EMAIL] to [EMAIL="mailpro@yahoo.com"]mailpro@yahoo.com[/EMAIL]. I don't know how to realize it with postfix. Also it would be nice if i dont have to create a lot of linuxusers for each smtp-account.

[IMG]http://www.foopara.de/example.png[/IMG]

---

### Post by SeijiSensei on 2011-04-25
> **vralfy said:**
> I'm using thunderbird and I'm sending a mail as user@littleserver. The littleserver archives the mail an send it via googlemail as [EMAIL="mailnewb@googlemail.com"]mailnewb@googlemail.com[/EMAIL] to [EMAIL="mailpro@yahoo.com"]mailpro@yahoo.com[/EMAIL]. I don't know how to realize it with postfix. Also it would be nice if i dont have to create a lot of linuxusers for each smtp-account.

Most email servers don't allow ordinary users to rewrite the From addresses in the way you want for security reasons. Creating the archived version and forwarding it along is pretty easy to accomplish using the standard aliasing mechanisms (/etc/aliases or /etc/mail/aliases):

```

user           \user,mailpro@yahoo.com

```

will keep a local copy ("\user") and send another to the mailpro account.  Then run "sudo newaliases" to update the alias database.

However the From address will be user@localserver.  I don't know how to rewrite that in Postfix.  With sendmail, you can use a "[genericstable]("http://www.madboa.com/geek/sendmail-genericstable/")" map to accomplish this if the user appears in /etc/mail/trusted-users.

---

### Post by vralfy on 2011-04-25
Is there an complete tutorial with sendmail which fits to my request?

Thanks anyway

---

### Post by moonport on 2011-04-25
> **vralfy said:**
> Is there an complete tutorial with sendmail which fits to my request?

Thanks anyway

Try this:
[http://www.sendmail.com/sm/open_source/docs/](http://www.sendmail.com/sm/open_source/docs/)

---

