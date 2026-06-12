---
title: "[SOLVED] subclipse unable to load default svn client"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by alfredio on 2008-09-11
If you are running Ubuntu 8.04 and you install Eclipse 3.4 with subclipse 1.4, you will probably get the "unable to load default svn client" error when trying to add a repository.

Here it is how I solved this problem. I assume that you have the 'subversion' and 'libsvn-java' packages already installed (if not, please do install them, and then follow the instructions).

1) Go to System --> Administration --> Software Sources
and under the "Updates" tab, check the hardy-backports updates. Close the window and update the package lists.
2) Run the update manager and update all packages (subversion will be updated from version 1.4 to version 1.5)
3) Edit the eclipse.ini file (it is located into the directory where you installed eclipse) by adding the following two lines, immediately after the "-vmargs" line
```

-Djava.library.path=/usr/share/java/
-Djava.library.path=/usr/lib/jni/

```

This should do the job, next time you start eclipse, it should correctly add your existing repository.

Please post comments if you have any trouble.

Cheers!

---

### Post by Vesperatus on 2008-09-11
Installed Ubuntu 7.10 and did the upgrade to 8.04. Insalled Eclipse and subversion then subclipse and ran into that issue.


Did what you said and it works now.

I had to find the eclipse.ini file however. I installed Eclipse using apt-get and my .ini file was under :

```
/usr/lib/eclipse/eclipse.ini
```

Thank you.

---

### Post by feydrutha on 2008-10-21
I don't really want to install all the backports. I'm not so sure they are as stable as the normal packages (I may be wrong on this, I guess..), even though subversion 1.5 is cool. 

Anyhow if you also don't want the backports another solution is to use version 1.2 of subclipse. Just use this eclipse update url:

[http://subclipse.tigris.org/update_1.2.x](http://subclipse.tigris.org/update_1.2.x)

---

### Post by naaka on 2008-10-27
Hi,
I have the following configuration:

eclipse 3.4
subclipse 1.4.5
subversion client adapter 1.5.2
javaHL 1.5.2.1

and the following subversion and libsvn-java package version (from backports):
1.5.1.dfsg1-1ubuntu2~hardy2

and had the message:

!ENTRY org.tigris.subversion.subclipse.core 4 -6 2008-10-22 15:43:23.344
!MESSAGE Unable to load default SVN Client

I added to the path of java library in eclipse.ini the specified locations.

Now i see javaHl in windows -> preferences -> team -> svn, and the log disapperaed.

Yet, i still cannot access my repository (right click on a project and go to team, no svn commands availables) and in progress bar still have "Sinchronizing task list (sleeping)".


Can you help ?


Thanks

---

### Post by Steve- on 2008-11-01
> **alfredio said:**
> Edit the eclipse.ini file (it is located into the directory where you installed eclipse) by adding the following two lines, immediately after the "-vmargs" line
```

-Djava.library.path=/usr/share/java/
-Djava.library.path=/usr/lib/jni/

```


I can confirm this works for Ubuntu 8.10, Eclipse 3.4.1 and svn 1.5.1

Thanks

---

### Post by meindian523 on 2008-11-01
Please mark the thread solved.

---

### Post by jradd on 2008-11-14
I just tried this with Ubuntu 8.10 using the default install of eclipse 3.2.  It does not work with this version, the steps above make no difference.

---

### Post by ajaygautam on 2008-12-31
> **jradd said:**
> I just tried this with Ubuntu 8.10 using the default install of eclipse 3.2.  It does not work with this version, the steps above make no difference.

I just ran into the same problem: Ubuntu 8.10 w/ Eclipse 3.4 - updating eclipse.ini has no side effect.

After some debugging, I noticed that my custom gnome launch icon was specifying "-vmargs" on the command line itself, which was rendering the vmargs from eclipse.ini useless.

Fixed by removing vmargs from eclipse launch command.

Check yours for similar error too.

Good luck

Ajay

---

### Post by ajaygautam on 2008-12-31
> **alfredio said:**
> 
[...]
 I assume that you have the 'subversion' and 'libsvn-java' packages already installed (if not, please do install them, and then follow the instructions).

[...]
3) Edit the eclipse.ini file (it is located into the directory where you installed eclipse) by adding the following two lines, immediately after the "-vmargs" line
```

-Djava.library.path=/usr/share/java/
-Djava.library.path=/usr/lib/jni/

```
[...]


PS: Thanks alfredio for your fix. I confirm that this works with 8.10 / Eclipse 3.4

Ajay

---

### Post by rpk180 on 2009-03-21
> **ajaygautam said:**
> PS: Thanks alfredio for your fix. I confirm that this works with 8.10 / Eclipse 3.4

Ajay

Hmmm, I'm unable to get this working with 8.10 / Eclipse 3.2 (via aptitude) or Eclipse 3.4 (from downloaded compressed tarball).  Here's my eclipse.ini from the 3.4 install:

```
$ more eclipse.ini
-showsplash
org.eclipse.platform
-framework
plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
-vmargs
-Djava.library.path=/usr/share/java/
-Djava.library.path=/usr/lib/jni/
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-XX:MaxPermSize=256m
```

I'm running eclipse from the commandline without any extra parameters ... any other suggestions?

---

### Post by kernco on 2009-03-25
This solution isn't working for me either.  I'm running Ubuntu 8.04, Eclipse 3.4.2, Subversion 1.5.1, and Subclipse 1.4.8.

---

### Post by billy61 on 2009-03-31
this solution also isnt working for me.  I have ubuntu 8.10 eclipse 3.4 and subversion 1.5.1

---

### Post by Mugatu on 2009-04-02
I had the same exact problem.  I'm running Ubuntu 8.10 and the default versions of Eclipse (3.2.2) and subversion (1.5.1) that I installed without changing the software sources/repositories.

[COLOR="Sienna"]PROBLEM:[/COLOR] (skip to the bottom to see the solution)
The problem's definitely with JavaHL ([http://subclipse.tigris.org/wiki/JavaHL](http://subclipse.tigris.org/wiki/JavaHL)).  It's installed on my system (via the libsvn-java package):

```
$ sudo aptitude install libsvn-java
$ sudo updatedb
$ locate libsvnjavahl
/usr/lib/jni/libsvnjavahl-1.so
/usr/lib/jni/libsvnjavahl-1.so.0
/usr/lib/jni/libsvnjavahl-1.so.0.0.0
```

I added this to my /usr/lib/eclipse/eclipse.ini right after "-vmargs":

```
-Djava.library.path=/usr/share/java/
-Djava.library.path=/usr/lib/jni/
```

I'm pretty sure it's set up correctly in Eclipse; when I click on Help --> About Eclipse SDK --> Configuration Details, I see the line:

eclipse.vmargs=-Djava.library.path=/usr/lib/jni

But somehow Subclipse isn't seeing JavaHL; in Eclipse when I click on Window --> Preferences --> Team --> SVN, under "SVN interface," JavaHL is supposed to show up, but it doesn't.

[COLOR="Sienna"]SOLUTION:[/COLOR]
In Eclipse, click Help --> Software Updates --> Find and Install, Search for new features to install, --> Next

Make sure the Subclipse mirror is selected (see [http://subclipse.tigris.org/install.html](http://subclipse.tigris.org/install.html) for a list of mirrors) and click Finish

Under Subclipse, select SVNKit.  I had to have all the sub-options selected before it would work (SVNKit Client Adapter, SVNKit Library, JNA Library)

Install those, restart, et voilà, that should do the trick!

---

### Post by archange on 2009-04-03
Hi,

none of the previous solutions work for me. I still have the message "Unable to load default svn client".

I'm using Ubuntu Intrepid 8.10. So it is subversion 1.5 which is installed.
I tried eclipse 3.2 from repositories and a manual installation of Ganymede.

I installed subclipsed 1.6, I installed the svn toolkit, I tried the modification of the eclipse.ini file and I still have this error.

When I go on google, the main solution is the modification of the .ini file, I would like to know if someone has an other solution :)

Cheers,

Archange

---

### Post by archange on 2009-04-03
I found a solution : use subclipse 1.2 instead of 1.6. But it's not a good one cause I would like to use the last available version.
So if someone has an idea, I'll take it.

---

### Post by merike on 2009-04-03
> **archange said:**
> I found a solution : use subclipse 1.2 instead of 1.6. But it's not a good one cause I would like to use the last available version.
So if someone has an idea, I'll take it.

1.6 didn't work for me either, 1.4 did.

---

### Post by Mugatu on 2009-04-13
Okay, I was using the default version of eclipse that I installed using aptitude (3.2.2-5ubuntu2), but I was having too many problems with other plugins.  So far my only complaint with Ubuntu is the Eclipse package is outdated and there aren't many plugins in the repositories (PyDev is the only one I use that I found in the repositories).

So anyway, finally I just gave up, went to [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/), clicked on "Eclipse Packages," and downloaded Eclipse Classic 3.4.2.

Subclipse requires Subversion and JavaHL.  As already mentioned, JavaHL in Ubuntu is provided by the libsvn-java package, so I installed it:

```
$ sudo aptitude install libsvn-java
```

I installed Subversion, and then checked what version I have:

```
$ sudo aptitude install subversion
$ svn --version
svn, version 1.5.1 (r32289)
```

According to [http://subclipse.tigris.org/wiki/JavaHL](http://subclipse.tigris.org/wiki/JavaHL), because I have Subversion 1.5.x, I need Subclipse 1.4.x (each version of Subclipse is designed to work with a specific version of Subversion)

Following the install instructions from [http://subclipse.tigris.org/servlets/ProjectProcess?pageID=p4wYuA](http://subclipse.tigris.org/servlets/ProjectProcess?pageID=p4wYuA), the update site for Subclipse 1.4.x is [http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x).  I added that site to my software updates, and under Subclipse I installed Subclipse, Subversion Client Adapter, and Subversion Native Library Adapter (JavaHL).

I restarted Eclipse, and tried to browse an SVN repository, and got the good old "unable to load default svn client" error.  So, I modified the application launcher command and appended this:

```
-vmargs -Djava.library.path=/usr/lib/jni
```

So, since I installed eclipse in /opt (that's just where I felt like installing it), my complete command for running Eclipse is:

```
/opt/eclipse/eclipse -vmargs -Djava.library.path=/usr/lib/jni
```

I started it up, and no more errors.  Plus, now I've got the latest version of Eclipse.  :)

---

### Post by laserjim on 2009-04-14
I had the same problem

Ubuntu 8.10
svn, version 1.5.1 (r32289)
Eclipse Platform 3.4.2

What worked for me was:
Delete all of eclipse, including the workspace, binaries, and plugins
sudo apt-get install subversion
sudo apt-get install libsvn-java
Download and extract the eclipse tarball
Install [http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x) (1.6 did not work) by going to Help>Software Updates
Restart eclipse
Checkout subversion project :)

---

### Post by Vesperatus on 2009-04-30
Hi guys, 

I installed my laptop with 8.10 and then updated to 9.04. I had the error and what is really important is to install libsvn-java :

```
 sudo aptitude install libsvn-java
```

That fixed it.

---

### Post by lbharti on 2009-05-17
Ubuntu Hardy Heron (8.04)
java version 1.6
Eclipse 3.4
subclipse 1.4.x

Installed:
apt-get install libsvn-java

Tested:
./eclipse -vmargs -Djava.library.path=/usr/lib/jni

Added to eclipse.ini in installation path (I have a custom installation)

-vmargs
-Djava.library.path=/usr/lib/jni

Done!
Works with javaHL 1.5.1 (r32289)

Hope this helps someone.

---

### Post by Kilnr on 2009-07-24
> **Mugatu said:**
> 
[COLOR="Sienna"]SOLUTION:[/COLOR]
In Eclipse, click Help --> Software Updates --> Find and Install, Search for new features to install, --> Next

Make sure the Subclipse mirror is selected (see [http://subclipse.tigris.org/install.html](http://subclipse.tigris.org/install.html) for a list of mirrors) and click Finish

Under Subclipse, select SVNKit.  I had to have all the sub-options selected before it would work (SVNKit Client Adapter, SVNKit Library, JNA Library)

Install those, restart, et voilà, that should do the trick!

That's what did the trick for me! (After installing libsvn-java and editing eclipse.ini.)

Cheers!

---

### Post by brunogirin on 2009-09-22
This did the trick for me on Jaunty (without needing the backport as the version of svn in Jaunty is already 1.5.4). Thanks!

---

### Post by togo59 on 2009-12-09
> **Vesperatus said:**
> Hi guys, 

I installed my laptop with 8.10 and then updated to 9.04. I had the error and what is really important is to install libsvn-java :

```
 sudo aptitude install libsvn-java
```

That fixed it.

The above did it for me, everything else I did from within Eclipse.

---

### Post by LeFou on 2010-01-11
Nope.

I'm on a dell mini 13 with hardy preinstalled. Finally got subversion commands when I realized (following this thread's advice) that "Not required" for SVNKit means "You have to have this".

Anyway, I can now right-click files and Team->update to Head, etc., but (and this is a big but)

I can't open code files to, y'know, edit them. Do programming. That sort of thing.

The Error log (tangent: I have to switch to the Plugin Development Perspective to see the error log?!) says

Problems occurred when invoking code from plugin org.eclipse.jface

I don't know what that plugin is.


UPDATE: per another post here i tried
sudo apt-get install libsvn-java

and got

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsvn-java: Depends: libsvn1 (= 1.4.6dfsg1-2ubuntu1) but 1.5.1dfsg1-1ubuntu2~hardy2 is to be installed
E: Broken packages

---

