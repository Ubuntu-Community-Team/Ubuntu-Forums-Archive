---
title: "amavisd-new identifies mail from me a spam"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2018-08-27
I'm using my own mail server for incoming mail and use amazon as the outgoing mail server
I've configured postfix and amavis about four years ago and evertything has been working fine.
After upgrading the server to 18.10 LTS recently I found that I cannot send emails from a mail client to myself as the mail is no identifie as spam

```
Aug 27 20:54:14 llmail amavis[2312]: (02312-01) Blocked SPAM {DiscardedOpenRelay,Quarantined}, [8.23.224.50]:3146 [54.240.8.208] <010001657afa1959-e377ce5c-ef4d-4616-a019-dd2904b353ca-000000@amazonses.com> -> <poldi@zudiewiener.com>, quarantine: A/spam-AYulRk6sX83G.gz, Queue-ID: 249D51FECE, Message-ID: <010001657afa1959-e377ce5c-ef4d-4616-a019-dd2904b353ca-000000@email.amazonses.com>, mail_id: AYulRk6sX83G, Hits: 6.561, size: 2321, dkim_sd=lrbxnn4xeflsy2e5j5jrbjbuoq4xuzum:zudiewiener.com,ug7nbtf4gccmlpwj322ax3p6ow6yfsug:amazonses.com, 6059 ms
A
```

I'd appreciate any ideas as to what I have to do to fix this.
Thanks

---

