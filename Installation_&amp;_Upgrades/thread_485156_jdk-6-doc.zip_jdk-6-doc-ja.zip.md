---
title: "jdk-6-doc.zip jdk-6-doc-ja.zip"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by OperaSinger on 2007-06-26
Every time I try to download something I get this message:
> This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

And every time I try to download, I get the EXACT same error message. I have just been saying "no," and most applications have been running fine. But I don't want to take the chance of any future problems. 

How should I fix this?

---

### Post by olejorgen on 2007-06-27
If you want java-doc you need to follow the instructions.

If you just want the error message to disapear I would guess that uninstalling java-6-doc and java-6-doc-ja (or somthing similar) whould fix it.

---

### Post by n.aggel on 2007-08-18
uninstalling java-6-doc didn't solve the problem for me...

here is what i did ::

go to [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) and download jdk-6-doc.zip

then open a terminal and type "sudo nautilus", in the new browser window it appears, copy the downloaded file from desktop to /tmp.......

after i changed the owneship and the group  to root {but i don't know if this was necessary}

Then open synaptic and choose to install java-6-doc..

and voila, the problem goes away!

---

### Post by DonQuichote on 2007-08-24
Dear all,

I cannot install the java 6 SDK documentation. I run synaptic in console mode and understand the message it gives. But: if I follow the link, I cannot find the documentation that the message refers to. I need a non-update version of the documentation, and I can only see update versions. Searching the rest of the site also gave me no results. Does anyone know where exactly I can download a non-update version of the java 6 SDK documentation?

UPDATE:
I tried "java 6 SE documentation" and this seems to be the right one. I'm sorry to have bothered you too soon...

---

### Post by watkinsted on 2007-11-11
I'm with Don Quihote on this one.  I haven't found the documentation at [http://java.sun.com](http://java.sun.com) at all.  What I did i just unchecked it from my synaptic packagae manager.  Although, I did just reinstall Ubuntu due to a hard drive crash a little bit ago. Still researching a bunch of things I can't seem to find, and my respositories are in my sources list as they should, confused here lol.

---

### Post by tuskpc on 2007-11-17
Just follow n.aggel  instructions and it should work.  I downloaded it to my /home/tmp folder and 
$ chmod 755 jdk-6-doc-zip 
then I typed 
$mv jdk-6-doc-zip /tmp/
after that go back to synaptic where the terminal is asking to to try agian or abort.  Type Y and the file will be unzipped and stored where it belongs.

---

### Post by guitariste on 2007-11-24
hello every body i have the same problem but   i think that  [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)
don't work anymore =====> i can't dowload the jdk-6-doc.zip  :(
do you know an other site where i can download it please .
thks.

---

### Post by guitariste on 2007-11-25
euuhhhhhhh   i try   again today and everything is ok  so i download the .zip 
but the "sudo nautilus"   make this message:
[COLOR="Red"](nautilus:7683): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.[/COLOR]

so i copy the .zip manually to tmp   and it's  ok..........   i thing.
but i would like to know the cause of this error.

---

### Post by north-east-angler on 2008-03-21
it is there its under the name of something like JDK 6 Documentation

---

### Post by stormzen on 2008-03-22
No, it's not.  It looks like it's there, but when you click on the link, it brings you out a link to where you clicked on to get to that page...

---

### Post by whistlerspa on 2008-05-02
I can't find any trace of java-6-doc.zip on Java's website - where is it?

I found an alternative myself in the next post below

---

### Post by whistlerspa on 2008-05-02
> **stormzen said:**
> No, it's not.  It looks like it's there, but when you click on the link, it brings you out a link to where you clicked on to get to that page...


I found it on this mirror 

[http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html](http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html)

I then ran 'sudo nautilus' to copy it to /tmp and then reinstalled jre so that the files were extracted to /var/lib...

Next I found (on another post) that I needed to run  

'sudo update-alternatives --config java' and selected option 2. 

Frostwire now works for me. ( I uninstalled all the open java stuff but this may not be necessary).

---

### Post by eljefe on 2008-05-06
> **whistlerspa said:**
> I can't find any trace of java-6-doc.zip on Java's website - where is it?

I found an alternative myself in the next post below

The problem is actually in identifying the correct file on the Sun website.
As it says, if this is the first time you are installing Java, then DONT use the "update".
I must have downloaded, chrooted and copied  the wrong file about 3 times...

NOW I have found the correct one, it works perfectly.

Go here:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

**DONT** download this one: **JDK 6 Update 6**

**DO** download this one.**Java SE 6 Documentation**

The funny thing is that these 2 files are the same size, with the same name, so its easy to download the wrong one. ( **jdk-6-doc.zip** )

Do what "Pointone" said

sudo chown root:root jdk-6-doc.zip
sudo cp jdk-6-doc.zip /tmp

... then restart.

The confusion for me came by not being able to read instructions, getting sidetracked by the wrong download. I should have stuck with Icedtea Java, unfortunately is wasnt compatible with some new software I  loaded.

Cheers
jeff

---

### Post by LarsSikstrom on 2008-07-03
This is just to thank everybody, who has written in this thread and google, who brought me into it.
I am presently trying to get dosemu to work and that brought me the problem of the jdk-6-doc.zip file. All suggestions I read got me nowhere and that until I quite simply typed the name of the file into google. This got me into the thread.I followed the instructions in it; finding the file, downloading it, copying to /tmp giving the ownership to root and reistalling via Synaptic. 
What a lot of time this has saved!

Again many thanks to all involved!

Lars Sikstrom

---

