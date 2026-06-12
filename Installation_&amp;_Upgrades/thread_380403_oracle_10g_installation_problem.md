---
title: "oracle 10g installation problem"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by hitter on 2007-03-09
Hi there, Has any one installed oracle DB 10g enterprise edition(not XE) on ubuntu edgy sucessfully? I have been trying to install following these guides..

[http://linux.togaware.com/survivor/Oracle_10g.html]("http://linux.togaware.com/survivor/Oracle_10g.html")

[http://dizwell.com/prod/node/52]("http://dizwell.com/prod/node/52")

[www.spazidigitali.com/media/Oracle_su_ubuntu.pdf]("www.spazidigitali.com/media/Oracle_su_ubuntu.pdf")

well everything goes perfectly well until the oracle universal installer suddenly stops at 6%... i Dont know why it gets stuck suddenly.
I think i almost tried everything.. if this doesn't work then i think i have to move to fedora!!!!

Edit:
There is this oraInstall2007-03-10_01-24-55AM.err file.. which suppose to be a log of errors during the installation.. which has the following..

```
java.lang.NullPointerException
        at oracle.sysman.oii.oiif.oiifm.OiifmGraphicPageHandler.onView(OiifmGraphicPageHandler.java:801)
        at oracle.sysman.oii.oiif.oiifw.OiifwWizDialog.onViewPrivate(OiifwWizDialog.java:881)
        at oracle.sysman.oii.oiif.oiifw.OiifwWizDialog.access$000(OiifwWizDialog.java:329)
        at oracle.sysman.oii.oiif.oiifw.OiifwWizDialog$PrepareInventoryTree.run(OiifwWizDialog.java:1777)
        at java.lang.Thread.run(Unknown Source)
java.lang.NullPointerException
        at oracle.sysman.oii.oiin.OiinNetOps.addNICInfo(OiinNetOps.java:143)
        at oracle.sysman.oii.oiin.OiinNetOps.computeNICList(OiinNetOps.java:108)
        at oracle.sysman.oii.oiin.OiinNetOps.<init>(OiinNetOps.java:75)
        at oracle.sysman.oii.oiin.OiinNetOps.getNetOps(OiinNetOps.java:89)
        at oracle.sysman.oii.oiif.oiifw.OiifwHostNameWCDE.initialize(OiifwHostNameWCDE.java:111)
        at oracle.sysman.oii.oiif.oiifb.OiifbCondIterator.iterate(OiifbCondIterator.java:152)
        at oracle.sysman.oii.oiic.OiicDepWizEngine.doOperation(OiicDepWizEngine.java:424)
        at oracle.sysman.oii.oiif.oiifb.OiifbCondIterator.iterate(OiifbCondIterator.java:171)
        at oracle.sysman.oii.oiic.OiicPullSession.doOperation(OiicPullSession.java:1273)
        at oracle.sysman.oii.oiic.OiicSessionWrapper.doOperation(OiicSessionWrapper.java:289)
        at oracle.sysman.oii.oiic.OiicInstaller.run(OiicInstaller.java:546)
        at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:929)
        at oracle.sysman.oio.oioc.OiocOneClickInstaller.runInstaller(OiocOneClickInstaller.java:1921)
        at oracle.sysman.oio.oioc.OiocOneClickInstaller.main(OiocOneClickInstaller.java:2149)
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at oracle.sysman.oip.oipc.oipcr.OipcrRulesEngine.executeRule(OipcrRulesEngine.java:278)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executeCheck(OipcpPrereqChecker.java:495)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.runChecks(OipcpPrereqChecker.java:450)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executePrereqs(OipcpPrereqChecker.java:351)
        at oracle.sysman.oii.oiif.oiifw.OiifwPrereqWCDE$1.run(OiifwPrereqWCDE.java:650)
        at java.lang.Thread.run(Unknown Source)
Caused by: java.lang.NullPointerException
        at oracle.sysman.oip.oipc.oipcz.OipczPackagesChecks.checkPackages(OipczPackagesChecks.java:82)
        ... 10 more
java.util.zip.ZipException: oversubscribed literal/length tree
        at java.util.zip.InflaterInputStream.read(Unknown Source)
        at java.util.zip.ZipInputStream.read(Unknown Source)
        at java.io.FilterInputStream.read(Unknown Source)
        at oracle.sysman.oii.oiix.OiixFileOps.copyStream(OiixFileOps.java:1420)
        at oracle.sysman.oii.oiij.OiijFastJarExtracter.copyFileFromJar(OiijFastJarExtracter.java:258)
        at oracle.sysman.oii.oiij.OiijFastJarExtracter.copyJarContents(OiijFastJarExtracter.java:194)
        at oracle.sysman.oii.oiij.OiijFastJarExtracter.extract(OiijFastJarExtracter.java:143)
        at oracle.sysman.oii.oiij.OiijJarExtractQueue$OiijJarExtractWorker.run(OiijJarExtractQueue.java:341
```

---

