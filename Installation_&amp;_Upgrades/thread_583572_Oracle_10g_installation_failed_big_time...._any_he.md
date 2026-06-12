---
title: "Oracle 10g installation failed big time.... any help?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2007-10-20
hi all,
 i have installed (not successfully i m afraid) oracle 10g on Ubutu Dapper Drake following this link

[http://www.dizwell.com/prod/node/52?page=0%2C0](http://www.dizwell.com/prod/node/52?page=0%2C0)

installation went fine, however when i run the command dbca  at end of installation, i got following bad error

UnsatisfiedLinkError exception loading native library: njni10
Exception in thread "main" java.lang.UnsatisfiedLinkError: get
        at oracle.net.common.NetGetEnv.get(Native Method)
        at oracle.net.config.Config.getNetDir(Unknown Source)
        at oracle.net.config.Config.initConfig(Unknown Source)
        at oracle.net.config.Config.<init>(Unknown Source)
        at oracle.sysman.assistants.util.NetworkUtils.<init>(NetworkUtils.java:222)
        at oracle.sysman.assistants.util.step.StepContext.<init>(StepContext.java:255)
        at oracle.sysman.assistants.dbca.backend.Host.<init>(Host.java:682)
        at oracle.sysman.assistants.dbca.ui.UIHost.<init>(UIHost.java:205)
        at oracle.sysman.assistants.dbca.ui.InteractiveHost.<init>(InteractiveHost.java:54)
        at oracle.sysman.assistants.dbca.Dbca.getHost(Dbca.java:160)
        at oracle.sysman.assistants.dbca.Dbca.execute(Dbca.java:94)
        at oracle.sysman.assistants.dbca.Dbca.main(Dbca.java:180)
marco@worldcorp-laptop:/oracle/10g$


could anyone help me out?

thanks in advance and regards
 marco

---

