---
title: "Installing Postfix by following help.ubuntu.com"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by vhof on 2007-06-30
Hi, i'm newbie in postfix.

Failed to install by following this howto:
[[COLOR="Blue"]https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=%28postfix%29[/COLOR]]("https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=%28postfix%29")

Here's exactly what I did:


```
telnet localhost 25
```

Postfix will prompt like following in the terminal so that you can use to type SMTP commands.

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 valhoffman ESMTP Postfix (Ubuntu)
```


Type the following code segment in Postfix's prompt.

```
ehlo localhost
mail from: fmaster@localhost
rcpt to: fmaster@localhost
data
Subjet: My first mail on Postfix
Hi,
Are you there?
regards,
Admin
. 
quit 
```


and then,

```
su - fmaster
mail
```

i got
```
No mail for fmaster
```


I don't know also if I need to own a domain name like blablabla.com, because that's what the howto says..

Ok, help is greatly appreciated!

Thanks!

---

