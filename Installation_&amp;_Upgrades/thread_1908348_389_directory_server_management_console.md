---
title: "389 directory server management console"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by haschas on 2012-01-13
Hello there,

I hope it's right place to post my problem.

Few days ago I installed 389 directory server, management console, installation was successful, without any errors or something.

But when I try to launch, it fails with an error:
```

Exception in thread "main" java.lang.UnsatisfiedLinkError: org.mozilla.jss.CryptoManager.initializeAllNative(Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;ZLjava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;ZLjava/lang/String;Ljava/lang/String;ZZZZZZZZZZZ)V
    at org.mozilla.jss.CryptoManager.initializeAllNative(Native Method)
    at org.mozilla.jss.CryptoManager.initialize(CryptoManager.java:990)
    at org.mozilla.jss.CryptoManager.initialize(CryptoManager.java:956)
    at com.netscape.management.client.util.UtilConsoleGlobals.initJSS(Unknown Source)
    at com.netscape.management.client.comm.HttpsChannel.<clinit>(Unknown Source)
    at com.netscape.management.client.comm.HttpManager.createChannel(Unknown Source)
    at com.netscape.management.client.comm.CommManager.send(Unknown Source)
    at com.netscape.management.client.comm.CommManager.send(Unknown Source)
    at com.netscape.management.client.comm.HttpManager.get(Unknown Source)
    at com.netscape.management.client.console.Console.invoke_task(Unknown Source)
    at com.netscape.management.client.console.Console.authenticate_user(Unknown Source)
    at com.netscape.management.client.console.Console.<init>(Unknown Source)
    at com.netscape.management.client.console.Console.main(Unknown Source)

```Tried to look if it's everything alright with paths.

For installation I used this: ```
https://help.ubuntu.com/community/FedoraDirectoryServer#Installation_of_389_Directory_Server_under_Ubuntu_11.10_Oneiric_Ocelot
```Also installed some other libs, packages (jss, openjdk).

Maybe someone had this problem, and could help to deal with it, or maybe give some information, because i can't find anything similar to this.

Thanks ;)

---

### Post by dacutelittlebear on 2012-02-27
Hi!
I also followed your recipe and can't even get the console started.
What command did you use to start it?

My install went without a hitch, but I'm beginning to think that I may not have had the correct packages installed at all. I've been looking all over for 389-ds-console and idm but there's nothing...

---

