---
title: "Error installing star office"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by ivanatal on 2007-06-10
Hi!

My name is Ivan and I was triing to install StarOffice. I downloaded the installation file from the site of Sun Microsystems: file.sh. I opened this file and extracted its content.  So I saw 2 files ("setup" and "install.class") and 3 folders("licenses", "readmes" and "RPMS"). I tried to open the "install.class", but I couldn't. So I tried to open "setup" in the Terminal, appearing this:

ivan@ivan-desktop:~$ /home/ivan/MyDownloads/aa/setup
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
InvocationTargetException in ArchiveReader constructornull
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        ... 7 more
Target Exception Trace:
java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
        at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
        at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
        at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
        at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
        at install.<init>(ArchiveClassLoader.java:143)
        at install.main(ArchiveClassLoader.java:1263)
ivan@ivan-desktop:~$ 




Anyone can help me?

Thank you.

---

### Post by coffeecat on 2007-06-10
Er - I have to ask this. Why are you trying to install the commercial Star Office when its free cousin - Open Office - comes with a default install of Ubuntu?

Having said that, could you provide some more information. The 'RPMS' folder suggests you have got a version for rpm-based Linux. Ubuntu is deb-based and needs different packages. I've had a quick look on the Star-Office website but I couldn't find the download page. Can you give a link, so we can see what you downloaded?

---

### Post by ivanatal on 2007-06-10
Thank you for your answer, coffecat.

I want to install StarOffice, because my presentations made on PowerPoint don't run well on OpenOffice. A friend told me that the StarOffice is better, so I looked at the internet and I saw that Star Office 8 is free for students. I took a screenshot of the page:
[IMG]http://bp2.blogger.com/_0SgKS7CXyqE/Rmv6j-KCaoI/AAAAAAAAAAs/X8fAfUNiu30/s1600/SO.png[/IMG]

I downloaded the fifth link (underlined).

Thank you.

---

### Post by coffeecat on 2007-06-10
> **ivanatal said:**
> I downloaded the fifth link (underlined).

Where?

You need to provide a link.

---

### Post by ivanatal on 2007-06-10
[https://sdlc1d.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=A37D41C7E2F5DE96ED14934AE5257D08;jsessionid=A37D41C7E2F5DE96ED14934AE5257D08](https://sdlc1d.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=A37D41C7E2F5DE96ED14934AE5257D08;jsessionid=A37D41C7E2F5DE96ED14934AE5257D08)

---

### Post by coffeecat on 2007-06-11
No, that link gives me a login page.

I'm trying to see if you've downloaded a compatible version of StarOffice. There are several different packages types for installing apps in the Linux world, Is that 'setup' program a shell script? If it is, then you could post it to this forum using the 'Manage Attachments' button.

You see, I mentioned the RPMS folder in an earlier post but you didn't respond. The rpm package is used by Fedora, Suse and Mandriva among others. It simply won't work in Debian-based distros such as Ubuntu.

One last question - I see there's a readme folder. Did you read the documentation in it?

---

### Post by ivanatal on 2007-06-11
Coffeecat, thank you again!

That page of the Sun Microsystems is for students. You have to join in the site to have accsess to the download page.

I am now in another situation.

I used "alien" to convert the rpm files. They went to the folder /opt/staroffice8. I uninstalled the openoffice. Now I can open my files in the staroffice, but they are not associated with the programs of the staroffice. For example, I have to open the program and so open the file by the program. The icons of the staroffice are not displayed at the ubuntu menu.

What can I do now? How can I associate the files .doc, .ppt etc with the staroffice? Do I have to reinstall it? How?

Bye.

---

### Post by coffeecat on 2007-06-12
Ah - you used alien. I wasn't going to add a layer of complication but I'm glad it worked for you. The next two problems should be easily solved.

Are you using Ubuntu with gnome (default desktop has orange window decorations) or Kubuntu with KDE (blue)? 

If Gnome, go to System > Preferences > Main Menu and add a menu entry wherever you want. From your posting I guess the startup command is '/opt/staroffice8', but use whatever you are using at the terminal. You can even add an icon for the menu. Press the icon button and add the path to the icon (if there is one). Have a look in /opt - StarOffice may have put one there somewhere.

For KDE, simply right-click on the main kde menu somewhere and choose 'Edit menu'

To associate a filetype in KDE, right-click on file, choose 'open with', choose the preferred app and tick the 'remember application association...' tick-box. I'm in kde at the moment and can't remember the gnome method (even though I use gnome most of the time :? ) but I'll post back when I've checked this.

---

### Post by coffeecat on 2007-06-12
Just to add to my last post. In gnome, right-click the file (type) you want to associate,  select 'Properties', then the 'Open With' tab and, hopefully, you'll be presented with either just Staroffice which you can tick or a choice and you can tick whichever you prefer.

A few additional thoughts. You needn't have uninstalled Open Office. The executables and libraries for Oo are in /usr and wouldn't conflict with StarOffice in /opt. Also, the file association business is dealt with by the gnome (or kde) desktop. It's quite a different situation from Windows. No registry - thank goodness. :)

A couple of tips. Once you've got yourself a menu entry for StarOffice, right-click it and you can add a launcher for it to the desktop and/or panel. Or right-click on the desktop or panel and add your own custom launcher.

---

### Post by ivanatal on 2007-06-12
Thank you!

I did what you said and it's working fine now. 

Now I have to associate a kind of file (ex., .doc) at a time. But it's ok.

Thank you again for your atention!

---

