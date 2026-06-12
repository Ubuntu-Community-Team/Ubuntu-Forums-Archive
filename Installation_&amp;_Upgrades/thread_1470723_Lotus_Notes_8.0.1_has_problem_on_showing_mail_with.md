---
title: "Lotus Notes 8.0.1 has problem on showing mail with 9.10 Karmic"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by achieving on 2010-05-03
I install Lotus Notes 8.0.1 on Karmic Ubuntu 9.10, the setup is successfully. However, the mail could not show correctly. 

the Home shows blank. The mail address could not show for each mail. And some html mail could not show at all.

Below are the console output.

05/03/2010 03:42:49 PM  Lotus Notes client started
2010/05/03 15:43:15.532 SEVERE err.csilabelprovider.fetchimage.exception ::class.method=com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run() ::thread=Worker-5 ::loggername=com.ibm.rcp.csiviews.providers.CSILabelProvider

    com.ibm.csi.types.ServiceException: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:295)
    at com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run(CSILabelProvider.java:862)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImageFromNotes(NotesImageProvider.java:390)
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImage(NotesImageProvider.java:293)
    at com.ibm.notes.images.internal.NotesImageProvider.getImage(NotesImageProvider.java:121)
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:284)
    ... 2 more
2010/05/03 15:43:15.602 SEVERE err.csilabelprovider.fetchimage.exception ::class.method=com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run() ::thread=Worker-12 ::loggername=com.ibm.rcp.csiviews.providers.CSILabelProvider

    com.ibm.csi.types.ServiceException: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:295)
    at com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run(CSILabelProvider.java:862)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImageFromNotes(NotesImageProvider.java:390)
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImage(NotesImageProvider.java:293)
    at com.ibm.notes.images.internal.NotesImageProvider.getImage(NotesImageProvider.java:121)
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:284)
    ... 2 more
2010/05/03 15:43:15.703 SEVERE err.csilabelprovider.fetchimage.exception ::class.method=com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run() ::thread=Worker-8 ::loggername=com.ibm.rcp.csiviews.providers.CSILabelProvider

    com.ibm.csi.types.ServiceException: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:295)
    at com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run(CSILabelProvider.java:862)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImageFromNotes(NotesImageProvider.java:390)
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImage(NotesImageProvider.java:293)
    at com.ibm.notes.images.internal.NotesImageProvider.getImage(NotesImageProvider.java:121)
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:284)
    ... 2 more
2010/05/03 15:43:15.879 SEVERE err.csilabelprovider.fetchimage.exception ::class.method=com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run() ::thread=Worker-0 ::loggername=com.ibm.rcp.csiviews.providers.CSILabelProvider

    com.ibm.csi.types.ServiceException: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:295)
    at com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run(CSILabelProvider.java:862)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImageFromNotes(NotesImageProvider.java:390)
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImage(NotesImageProvider.java:293)
    at com.ibm.notes.images.internal.NotesImageProvider.getImage(NotesImageProvider.java:121)
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:284)
    ... 2 more
2010/05/03 15:43:15.885 SEVERE err.csilabelprovider.fetchimage.exception ::class.method=com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run() ::thread=Worker-14 ::loggername=com.ibm.rcp.csiviews.providers.CSILabelProvider

    com.ibm.csi.types.ServiceException: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:295)
    at com.ibm.rcp.csiviews.providers.CSILabelProvider$1.run(CSILabelProvider.java:862)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: com.ibm.notes.images.ImageProviderException: Invalid or nonexistent document
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImageFromNotes(NotesImageProvider.java:390)
    at com.ibm.notes.images.internal.NotesImageProvider.getResourceImage(NotesImageProvider.java:293)
    at com.ibm.notes.images.internal.NotesImageProvider.getImage(NotesImageProvider.java:121)
    at com.ibm.csi.notes.internal.NotesDesignDelegate.getSharedImage(NotesDesignDelegate.java:284)
    ... 2 more
05/03/2010 03:43:19 PM  Agent Manager started


Could anyone help me?

---

### Post by Zanetta on 2011-04-19
Hello, I'm with the same problem. You have arrived at some solution?

---

