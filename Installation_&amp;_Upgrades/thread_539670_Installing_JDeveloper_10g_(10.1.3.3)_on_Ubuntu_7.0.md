---
title: "Installing JDeveloper 10g (10.1.3.3) on Ubuntu 7.04"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by RMoetwil on 2007-08-31
Hello,

I'm trying to install JDeveloper 10g (10.1.3.3) on Ubuntu 7.04.
Followed all the linux installing instructions.

I tried JDK 1.5 and 1.6 but can't get JDeveloper to work.

I can start up, get past the annoying hidden error window (for jdk 1.6) and get into the main window.
But there's were the problem starts. I only see the borders of the window. So no views and all of that kind.
If i use the key combination CTRL+O a file open window comes up (as expected) but after selecting a file the main window comes back blank again.

Someone experienced the same problem?

Greetings, Ronald

BTW Eclipse works fine :)

---

### Post by jnorthr on 2007-08-31
You may want to see if your actual jdk1.5 & 1.6 installations were successful. If thy were not, you may still be using jre included with ubuntu which (i've been told) is jdk1.4 so that may not support jdev feature set.

Try this : open a terminal window and try java -version to see what jre version you have. If it's not 1.5 or 1.6 your jdk install was not succesful.

---

### Post by RMoetwil on 2007-09-01
java -version gives me:

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Server VM (build 1.6.0-b105, mixed mode)

In my .xsession-errors file a spotted the following java error:

java.lang.NoClassDefFoundError: com/sun/jdi/Bootstrap
        at oracle.jdevimpl.debugger.jdi.DebugJDIConnector.getVersion(DebugJDIConnector.java:32)
        at oracle.jdevimpl.debugger.support.DebugFactory.<clinit>(DebugFactory.java:70)
        at oracle.jdevimpl.cm.dt.DatabaseAddin.initialize(DatabaseAddin.java:186)
        at oracle.ideimpl.extension.AddinManagerImpl.initializeAddin(AddinManagerImpl.java:425)
        at oracle.ideimpl.extension.AddinManagerImpl.initializeAddins(AddinManagerImpl.java:240)
        at oracle.ideimpl.extension.AddinManagerImpl.initProductAndUserAddins(AddinManagerImpl.java:154)
        at oracle.ide.IdeCore.initProductAndUserAddins(IdeCore.java:1431)
        at oracle.ide.IdeCore.startupImpl(IdeCore.java:1196)
        at oracle.ide.Ide.startup(Ide.java:674)
        at oracle.ideimpl.Main.start(Main.java:49)
        at oracle.ideimpl.Main.main(Main.java:25)

I noticed that us/bin/java pointed to link in my java 1.6 jre.
I changed that so that it points to my java_home/bin directory.
The error disappeared.
(I did discover that java_home/bin actually contains a link for java to ../jre/java :)  :?:)

I also created a shell script setting JDEV_HOME an PATH linking JDEV_HOME and my jdk but that didn't work either.

Some other details:
The screen is blank but not white! It's kind of light blue. The cursor changes when moving in the window frame so probably JDeveloper is getting my mouse input.
Could it be something related to java GUI (SWT,AWT) or maybe something todo with GNOME desktop or xterm?

---

### Post by RMoetwil on 2007-09-02
Problem solved! \\:D/

After my latest hunch relating to Swing or desktop or xterm i did some searching in the forum and found something similar related to the beryl manager.

Although I don't what that is ;-) I thought of the feature 'Desktop Effects' which I got enabled.

Disabling this solved my empty frame problem.

After starting up JDeveloper you can enable it again and it seems to stay stable.

Anyway, back to configuring my laptop with more linux and java software. ;-)

---

### Post by jnorthr on 2007-09-02
Nice one !! Did remember reading that beryl, and some desktop effects were 'experimental' - and this may have added to your woes. I tried them myself but my graphics card is too old.
BTW: on another thread i had asked a question, I was asked to mark the thread as 'solved'. It's a good habit to get into for everyone's sake.
See the 'Thread Tools' menu item above this post ? They tell me if you go to your original post you should hit that item and there is a 'solved' entry to mark this topic as closed.

Enjoy !!

---

