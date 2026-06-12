---
title: "Arduino installation problem in 11.10"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by vikram91 on 2012-05-28
I followed this tutorial for installing arduino: [http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/)

I installed Openjdk-6-jre, gcc-avr, avr-libc using synaptic package manager and allowed to install whatever extra it wanted to install.

Then now when i try to compile a code, i get this error: Cannot run program "/home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/avr-g++": java.io.IOException: error=13, Permission denied

Then i enabled the "Allow executing file as program" in permissions tab for that avr-g++ file. But now i get an error like this:

/home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/avr-g++: line 3: /home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/../bin.gcc/avr-g++: Permission denied
/home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/avr-g++: line 3: exec: /home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/../bin.gcc/avr-g++: cannot execute: Permission denied
/home/vikram/Desktop/arduino-1.0.1/hardware/tools/avr/bin/avr-g++ returned 126


I don't know what to do now.. Can any linux expert help me in this issue

I dont understand why it is so difficult to install even a software in linux

---

### Post by raja.genupula on 2012-05-28
open terminal and type ```
sudo -i
```then cd to the directory where you have placed that file . then run it as 

```
./<filename>
```

let us know what you got .

---

### Post by vikram91 on 2012-05-28
> **raja.genupula said:**
> open terminal and type ```
sudo -i
```then cd to the directory where you have placed that file . then run it as 

```
./<filename>
```

let us know what you got . I did as you said. Still i get the same error.

---

### Post by rollinns on 2012-06-13
Have you tried upgrading to Arduino IDE version 1.0.1?

I got Arduino version 1.0.1 to work today in 11.04.  I'm spelling it out to help you but also so if I have to do this again on another computer I can get it right, so if I add too many details it's just for my own reference.

Here's what I did:

**_A._** Open Synaptic Package Manager, search for "arduino" and install it and all it's dependencies.  This was version 0022 for me, I had it installed and was having trouble upgrading it to 1.0.1, but the rest is what upgraded it without too much hassle.

**_B._** Then I followed the info here:

[[COLOR="Blue"]http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/[/COLOR]]("http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/")

I got some errors but basically I followed the directions from step 4 to the end (yes, that page does have two step #4s) 
Those steps are:
> 4. After installation done, jdk and jre will install at /usr/lib/jvm/java-6-sun-1.6.0.06

5. Ubuntu help to create a java symbolic link and put in /usr/bin for shortcut access

4. type java -version, DONE !!
Post-Installation Setup

Set JAVA_HOME into environment variable

Copy following statement and append to /etc/profile or .bashrc file, make system set JAVA_HOME into system environment variable.

```
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06"
```


In my case I changed the last part to:
```
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"
```
since my version was java-6-sun-1.6.0.22, not java-6-sun-1.6.0.06

**_C._** Next I went back to Synaptic, and under the "Settings" menu choose  "Repositories", then the "Other Software" tab and added this line:
```
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ quantal main universe
```
then hit "close" and "Reload" on the main Synaptic window.

**_D._** In Synaptic, search for "arduino" again and install it and all it's dependencies (this time it was just "arduino-core").  This was now version 1.0.1.   DO NOT CLICK ON "Mark All Upgrades" because this would only upgrade software in the "Universe" repository, and I'm not sure but I think it would break a whole lot of stuff.

**_E._** Still in Synaptic, and under the "Settings" menu choose  "Repositories"again, then the "Other Software" tab and UNCHECK this line:
```
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ quantal main universe
```
when it's highlighted, the click on "Remove".  If you see another line above or below it that says the same thing with "(Source code)" at the end, then UNCHECK and remove it also. Then hit "close" and "Reload" on the main Synaptic window.

At this point I went to the main Ubuntu "Applications" menu in the corner of my screen, clicked "Electronics", then "Arduino IDE" it took several seconds then showed up as version 1.0.1


I hope this works for you.

Rollinns

---

### Post by vikram91 on 2012-06-15
> **rollinns said:**
> Have you tried upgrading to Arduino IDE version 1.0.1?

I got Arduino version 1.0.1 to work today in 11.04.  I'm spelling it out to help you but also so if I have to do this again on another computer I can get it right, so if I add too many details it's just for my own reference.

Here's what I did:

**_A._** Open Synaptic Package Manager, search for "arduino" and install it and all it's dependencies.  This was version 0022 for me, I had it installed and was having trouble upgrading it to 1.0.1, but the rest is what upgraded it without too much hassle.

**_B._** Then I followed the info here:

[[COLOR="Blue"]http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/[/COLOR]]("http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/")

I got some errors but basically I followed the directions from step 4 to the end (yes, that page does have two step #4s) 
Those steps are:

In my case I changed the last part to:
```
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"
```
since my version was java-6-sun-1.6.0.22, not java-6-sun-1.6.0.06

**_C._** Next I went back to Synaptic, and under the "Settings" menu choose  "Repositories", then the "Other Software" tab and added this line:
```
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ quantal main universe
```
then hit "close" and "Reload" on the main Synaptic window.

**_D._** In Synaptic, search for "arduino" again and install it and all it's dependencies (this time it was just "arduino-core").  This was now version 1.0.1.   DO NOT CLICK ON "Mark All Upgrades" because this would only upgrade software in the "Universe" repository, and I'm not sure but I think it would break a whole lot of stuff.

**_E._** Still in Synaptic, and under the "Settings" menu choose  "Repositories"again, then the "Other Software" tab and UNCHECK this line:
```
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ quantal main universe
```
when it's highlighted, the click on "Remove".  If you see another line above or below it that says the same thing with "(Source code)" at the end, then UNCHECK and remove it also. Then hit "close" and "Reload" on the main Synaptic window.

At this point I went to the main Ubuntu "Applications" menu in the corner of my screen, clicked "Electronics", then "Arduino IDE" it took several seconds then showed up as version 1.0.1


I hope this works for you.

Rollinns

Actually my problem was solved long back. My mistake was " i extracted the arduino archive in windows 7 and then copied the extracted folder to ubuntu which caused all the permission errors. When i extracted the archive in Ubuntu, i didnt get any errors.

And in your method, I doubt if the B) step is required. Because when we install arduino from ubuntu software center, it automatically installs openjdk. I'm not sure if the synaptics installs it or not.

Actually a simple method of installing arduino 1.0.1 would be:

1) Install arduino 0022 from ubuntu software center. It installs everything it requires
2) Download arduino 1.0.1 from the arduino website and extract it inside ubuntu itself.
3) Just run it :)

---

### Post by rollinns on 2012-06-15
> Actually a simple method of installing arduino 1.0.1 would be:

1) Install arduino 0022 from ubuntu software center. It installs everything it requires
2) Download arduino 1.0.1 from the arduino website and extract it inside ubuntu itself.
3) Just run it 

I tried that and got an error which needed the fix in step B to fix.  But I do agree that your way would be much more simple.
[http://ubuntuforums.org/images/smilies/eusa_doh.gif](http://ubuntuforums.org/images/smilies/eusa_doh.gif)

---

### Post by vikram91 on 2012-06-16
> **rollinns said:**
> I tried that and got an error which needed the fix in step B to fix.  But I do agree that your way would be much more simple.
[http://ubuntuforums.org/images/smilies/eusa_doh.gif](http://ubuntuforums.org/images/smilies/eusa_doh.gif)

I did that after a fresh install of ubuntu 11.10 64-bit and it gave me no errors

---

