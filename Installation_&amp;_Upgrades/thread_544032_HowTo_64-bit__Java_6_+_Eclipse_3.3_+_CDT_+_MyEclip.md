---
title: "HowTo: 64-bit  Java 6 + Eclipse 3.3 + CDT + MyEclipseIDE installation"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-09-05
Apologies if this has been covered elsewhere, but I couldn't find anything authoritative.

I thought I'd confirm for those wondering about installing on 64-bit systems that I've had no problems installing and running MyEclipse 6.0 GA with Eclipse 3.3 64-bit on Sun Java 1.6 64-bit, on Ubuntu Gutsy (tribe-5) 64-bit.

I use the Eclipse CDT (C/C++) perspective extensively for Ubuntu GNU/Linux kernel development hacking and debugging.

I took the precaution of renaming the existing Eclipse (32-bit) user settings directory before I started to prevent any type-size mishaps.

I also customised the location of Eclipse 3.3 so it could co-exist with previous installations until I was sure it was stable (I run 32-bit and 64-bit installations with the same /home mount).

Here's the sequence of shell commands that captures the steps I took including configuration changes for performance. They could be inserted into a bash script and run that way rather than cut/paste to a terminal:
```
# protect any existing 32-bit configuration
mv  ~/.eclipse ~/.eclipse-32bit

# install the JDK, which depends on sun-java6-jre and sun-java6-bin
sudo apt-get install sun-java6-jdk

# ensure Sun Java6 is the default java
update-alternatives --config java

# download Eclipse 3.3 64-bit for Linux
wget http://www.mirrorservice.org/sites/download.eclipse.org/eclipseMirror/eclipse/downloads/drops/R-3.3-200706251500/eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz

# fetch the standard Ubuntu Eclipse 3.2.x 64-bit starter script and docs
wget http://archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse_3.2.2-0ubuntu3_amd64.deb

# all we want is /usr/bin/eclipse
mkdir /tmp/eclipse;
dpkg -x eclipse_3.2.2-0ubuntu3_amd64.deb /tmp/eclipse

# fix-up the launcher script with our '3.3' specific values
sed -i -e 's:/usr/lib/eclipse/startup.jar::' \
   -e 's:/usr/lib/eclipse:/usr/lib/eclipse-3.3:' \
   -e 's:/usr/local/lib/eclipse:/usr/local/lib/eclipse-3.3:'  \
 /tmp/eclipse/usr/bin/eclipse

# rename, make it executable, and move it into place
mv /tmp/eclipse/usr/bin/eclipse /tmp/eclipse/usr/bin/eclipse-3.3
sudo cp /tmp/eclipse/usr/bin/eclipse-3.3 /usr/bin/
sudo chown root:root /usr/bin/eclipse-3.3
sudo chmod a+x /usr/bin/eclipse-3.3
# from now on eclipse 3.3 can be launched using the command "eclipse-3.3"

# copy the icons too
sudo cp /tmp/eclipse/usr/share/pixmaps/* /usr/share/pixmaps/

# create a separate directory for 3.3, to protect existing versions
sudo mkdir /usr/lib/eclipse-3.3
sudo tar -xzf eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz -C /usr/lib/eclipse-3.3

# create an extension location for installing Eclipse 3.3 features for all users
sudo mkdir /usr/local/lib/eclipse-3.3

# allow all users to install to the location
# this allows additional features to be installed without su privileges
sudo chown root:staff /usr/local/lib/eclipse-3.3
sudo chmod g+xw /usr/local/lib/eclipse-3.3
if [ "x$(egrep "staff:.*:${USER}" /etc/group)" = "x" ]; then  \
  sudo usermod -aG staff ${USER}; \
  echo "Added to group 'staff'. You will need to logout before this change will take effect"; \
fi

# download the MyEclipseIDE manual install archive 
wget http://downloads.myeclipseide.com/downloads/products/eworkbench/6.0GA/MyEclipse_6.0GA_E3.3_ManualInstall.zip 

# create a directory for MyEcliseIDE and install
sudo mkdir /usr/lib/myeclipse
sudo unzip MyEclipse_6.0GA_E3.3_ManualInstall.zip -d /usr/lib/myeclipse

# configure Eclipse for higher memory usage
if [ ! -e ~/.eclipse ]; then mkdir ~/.eclipse; fi
echo "$(update-alternatives --display java | grep 'link')" | sed -e 's/.*to /JAVA_HOME=/' -e 's/jre.*//' >> ~/.eclipse/eclipserc
echo -e "VMARGS=\"-Xms128m -Xmx512m -XX:PermSize=64M -XX:MaxPermSize=128M\"" >> ~/.eclipse/eclipserc

# configure Linux for more user file handles (Eclipse features can demand more than the default 1024)
sudo sh -c "echo  \"${USER} \t\thard \tnofile \t\t32768\" >> /etc/security/limits.conf"

# now start Eclipse
# watch for and deal with any error reports
eclipse-3.3

# The first thing to do is install all additional optional features such as the CDT (C/C++ tools)
# When asked where to install them, choose '/usr/local/lib/eclipse-3.3' so that platform features
# are available to everyone
# ** REMEMBER ** to do this you'll have needed to log-out/log-in to ensure you're a member of the 'staff' group

# Now add MyEclipseIDE from Help > Software Updates > Manage Configuration
# right-click "Eclipse SDK" and choose Add > Extension location...
# and navigate to '/usr/lib/myeclipse/eclipse'

# restart and update features as needed

# Now add any menu short-cuts to the display manager menus (Gnome, KDE, etc)
# command is /usr/bin/eclipse-3.3
# icons are in /usr/share/pixmaps/

```

---

### Post by nephish on 2007-09-21
thanks for this, great work

---

### Post by azbarcea on 2007-09-21
I didn't wanted myeclipse so i did'n installed it ... i just run the batch till ./eclipse-3.3
at the end I want an installation  64-bit Java 6 + Eclipse 3.3 + CDT + PDT installation

first i installed sun-java6-jdk, but when i launched eclipse-3.3 some error occurred: 
jvm/gcj .... notfound
java 1.4 ... notfound
java 1.5 ... notfound

i installed java 5 and that error didn't occur anymore, but

when i run *eclipse-3.3*, the following error occurs:

```

$ eclipse-3.3
using specified vm: /usr/lib/jvm/java-1.5.0-sun/
Invalid or corrupt jarfile /home/myname/

```

and a pop-up appears:
[HTML]
JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-Xms128m
-Xmx512m
-XX:PermSize=64M
-XX:MaxPermSize=128M
-jar /home/alex/
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /usr/lib/eclipse-3.3/eclipse
-name Eclipse
--launcher.library /usr/lib/eclipse-3.3/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.0.v20070606/eclipse_1017a.so
-startup /home/alex/
-exitdata 658013
-install /usr/lib/eclipse-3.3
-vm /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-Xms128m
-Xmx512m
-XX:PermSize=64M
-XX:MaxPermSize=128M
-jar /home/myname/
[/HTML]

any ideas?

---

### Post by azbarcea on 2007-09-21
somehow i manged to make it work ... but i'm sure is not the correct way!

i installed using adept the *eclipse-platform* and *eclipse-rcp*, and I run eclipse and the eclipse-3.3 Europa started.

I think that STARTUP variable was found at last ... but i'm not sure.
The good news is that it works, The bad news is that i don't know how it works!

---

### Post by oerd on 2007-09-27
I think there are some little errors on the script, but otherwise i did find it very useful.

The batch commands for moving the ubuntu .deb config files into /usr/bin/eclipse are buggy in that they should be ```
mv /tmp**/eclipse**/usr/bin ....  
```

As for the second posters problem I managed to solve the same errors by modifying the actual launching command from the eclipse ubuntu launcher (/usr/bin/eclipse). 
Mine looks like:
```

# Do the actual launch of Eclipse with the selected VM.
exec /usr/lib/eclipse/eclipse \
    -vm "${JAVACMD}" \
    -install "${INSTALL}" \
    ${CMDLINEARGS} \
    -vmargs -Djava.library.path=/usr/lib/jni \
            -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db \
            -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
            -Dosgi.locking=none ${VMARGS}

```
the -startup line is missing (after install) the eclipse 3.3 doesn't provide a startup.jar on the $ECLIPSE_HOME directory so it is useless. For that matter even launching /usr/lib/eclipse/eclipse from the shell works as long as you set the necessary defaults on your ~/.eclipse/eclipserc file. Don't see the need for all the definitions on the last four lines if we are going to use java-6-sun!

---

