---
title: "Eclipse SVN Problems"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-11
Just upgraded a Karmic installation to Lucid in which I use Eclipse integrated with SVN.

Upon launching Eclipse, I see that my SVN repos have disappeared and that Eclipse no longer has SVN integration.

I try to update the SVN plugins and I get the following error:
```

Current configuration contains errors that are not corrected by the requested operation and more errors would be introduced. See details for more information.
  ----- Current configuration problems -----
    Subclipse (Required) (1.6.5) requires plug-in "org.tigris.subversion.clientadapter (1.6.0)", or equivalent.
    SVNKit Client Adapter (Not required) (1.6.4) requires plug-in "org.tigris.subversion.clientadapter (1.6.4)", or equivalent.
  ----- Configuration problems after the operation -----
    Subclipse Integration for Mylyn 3.x (Optional) (3.0.0) requires plug-in "org.eclipse.mylyn.tasks.core (3.0.0)", or compatible.
    Subversion Revision Graph (1.0.7) requires plug-in "org.eclipse.draw2d (3.2.0)", or later version.

```

Any ideas??  Can't seem to get anywhere with it.  I may try uninstall and reinstall eclipse?

---

### Post by Kenny_Strawn on 2010-02-11
When you upgraded to Lucid, Update Manager probably removed your plugins. Try reinstalling them via Apt-Get in the command line.

---

### Post by JCoster on 2010-02-12
Hey, thanks for your quick reply.  Which plugins would I need to install via apt-get to get SVN working again?

Cheers,
JC

---

### Post by JCoster on 2010-02-14
bump (i apologise)

---

### Post by JCoster on 2010-02-15
Well, I finally managed to get this resolved this afternoon by downloading the latest version of eclipse from the website, running this version in a directory on my desktop, downloading and installing the plugin, and then merging the files over the ones in /usr/lib/eclipse/ (i.e. my repo install).

no amount of apt-get remove/purge and reinstallation of eclipse would fix this until I did the steps outlined above.

---

