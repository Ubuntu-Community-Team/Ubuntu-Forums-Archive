---
title: "make path for uisp script installation for tinyos in ubuntu"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by newsman on 2006-11-10
I am trying to install tinyos ([www.tinyos.net](www.tinyos.net)) on ubuntu for my work using chad metcalfe's guide ([http://www.chadmetcalf.com/tinyos-1x-on-ubuntu/](http://www.chadmetcalf.com/tinyos-1x-on-ubuntu/))

There is one major difference between me and him.. He is using sky tmote kits and i am using crossbow kits. 

thus i need to install uisp script..for this reason i looked at mathews'guide;
[http://www.crhc.uiuc.edu/~mjmille2/howtos/installing-tinyos-for-telos-on-linux/](http://www.crhc.uiuc.edu/~mjmille2/howtos/installing-tinyos-for-telos-on-linux/)


step 12 on his guide:

cd $TOSROOT/tools/src/uisp;
./COMPILE;
make install;

I get the following error:

./COMPILE: line 8: gnumake: command not found
./COMPILE: line 8: gmake: command not found
make: *** No targets specified and no makefile found.  Stop. 

I was told i need to include path to make/gmake/gnumake in my bashrc file.


First question... how do i get gmake and gnumake???

Second question... how do i add it to my bashrc file???


I looke at synaptic package manager, the closest i came to programe for gmake and gnumake is actually "make"

on querying i got the following description and  files that were installed.  Is this the gmake or gnumake required???

The GNU version of the "make" utility.
GNU Make is a program that determines which pieces of a large
program need to be recompiled and issues the commands to recompile
them, when necessary. More information about GNU Make can be
found in the `make' Info page. The upstream sources for this package
are available at the location [ftp://ftp.gnu.org/gnu/make/](ftp://ftp.gnu.org/gnu/make/)

/.
/usr
/usr/bin
/usr/bin/make
/usr/lib
/usr/share
/usr/share/info
/usr/share/info/make.info-2.gz
/usr/share/info/make.info.gz
/usr/share/info/make.info-1.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/make.1.gz
/usr/share/doc
/usr/share/doc/make
/usr/share/doc/make/changelog.Debian.gz
/usr/share/doc/make/changelog.gz
/usr/share/doc/make/NEWS.gz
/usr/share/doc/make/NEWS.Debian.gz
/usr/share/doc/make/copyright
/usr/share/doc/make/README.gz
/usr/share/doc/make/Explanations.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/make



Thank you.....

---

### Post by michael_gilroy on 2007-06-28
Apologies for the length of the reply. All of this is  based upon the instructions from:
[http://www.5secondfuse.com/tinyos/install.html](http://www.5secondfuse.com/tinyos/install.html)

I've been working with the crossbow motes having followed these instructions without any problems. 

Ubuntu Packages
In order to insure you have all the required packages, you'll need to add the universe and multiverse repositories.
Now you just need to add the packages.
sudo apt-get install cvs subversion autoconf automake1.9 python-dev  
sudo apt-get install g++-4.0 gperf swig sun-java5-jdk graphviz alien fakeroot
sudo apt-get install g++-3.4
Environment Variables
This is the most important and awkward step in getting tinyos to work in Linux. This guide sets up your development environment so you can use TinyOS 1.x, TinyOS 2.x, and Boomerang. To make life easy you can copy the file in Appendix 1 to your home directory. You'll need to add a line to your .bashrc to source this file on login. If you use a different shell it would be fairly trivial to change over.
# Add this to your .bashrc
if [ -f ~/.bash_tinyos ]; then
    . ~/.bash_tinyos
fi
This will allow you to switch between environments on fly.
metcalfc@TinyLaptop:~$ tos1
Setting up for TinyOS 1.x
... Do TinyOS 1.x work ...
metcalfc@TinyLaptop:~$ tos2
Setting up for TinyOS 2.x ...
... Do TinyOS 2.x work
metcalfc@TinyLaptop:~$ boomerang
Setting up for TinyOS 1.x with Boomerang
... Do TinyOS Boomerang work ...
Install TinyOS 1.x
cvs -d:pserver:anonymous@tinyos.cvs.sourceforge.net:/cvsroot/tinyos login
cvs -z3 -d:pserver:anonymous@tinyos.cvs.sourceforge.net:/cvsroot/tinyos co tinyos-1.x
sudo mv tinyos-1.x /opt
Install Boomerang
For the Moteiv specific Boomerang installation you'll need to get the files from Moteiv here. Its 185 megs so sit back and enjoy a coffee while you wait.
mkdir tmote
cp tmote-tools-2_0_4.zip tmote
cd tmote
cd common/rpms
fakeroot alien -d tinyos-moteiv-2.0.4-1.cygwin.noarch.rpm
sudo dpkg --install *.deb
rm -rf tmote
sudo chown -R $USER /opt/moteiv
Optional: Install TinyOS 2.x from CVS
I don't use this however it should work. You'll also need to update your .bash_tinyos to reflect where you put it.
cvs -d:pserver:anonymous@tinyos.cvs.sourceforge.net:/cvsroot/tinyos login
cvs -z3 -d:pserver:anonymous@tinyos.cvs.sourceforge.net:/cvsroot/tinyos co tinyos-2.x
cvs -z3 -d:pserver:anonymous@tinyos.cvs.sourceforge.net:/cvsroot/tinyos co tinyos-2.x-contrib
Java Serial Communications for TinyOS 1.x
You'll need to install TOSComm in order for your TinyOS 1.x Java toolchain to work. Yes, the TinyOS-tools package from TinyOS 2.x does this but it doesn't work for 1.x. And yes the two can coexist in your $JDKROOT. 
The installer detects the wrong location to install the files to because of the alternatives setup. Edit the JAVADIR rule in the $TOSROOT/beta/TOSComm/comm/Makefile with: 
JAVADIR=/usr/lib/jvm/java-1.5.0-sun
Now install it. We'll alias g++ to the correct version so we don't have to edit anymore makefiles.
alias g++=g++-3.4; cd $TOSROOT/beta/TOSComm; sudo make install
Other Java Configuration steps
Need to download and install IBM-JDK-1.4.2 and JAVACOMM-1.4.2 rpms  for tinyos 1.x
Convert both rpms to debs using alien command, for example: 
alien -d IBMJava2-142-ia32-SDK-1.4.2-1.0.i386.rpm 
Install debs on Ubuntu using dpkg command, for example: 
 sudo dpkg -i ibmjava2-142-ia32-sdk_1.4.2-8_i386.deb 
 sudo dpkg -i ibmjava2-javacomm_1.4.2-8_i386.deb 

Install TinyOS Tools
Download the rpm packages from [http://webs.cs.berkeley.edu/tos/dist-1.1.0/tools/linux](http://webs.cs.berkeley.edu/tos/dist-1.1.0/tools/linux), and what I downloaded was: 
avarice-2.0.20030825cvs-1.i386.rpm 
avr-binutils-2.13.2.1-1.i386.rpm 
avr-gcc-3.3tinyos-1.i386.rpm 
avr-libc-20030512cvs-1.i386.rpm 
graphviz-1.10-1.i386.rpm 
make-3.80tinyos-1.i386.rpm 
tinyos-tools-1.1.0-1.i386.rpm 
Install them using alien and dpkg 
Do NOT try upgrade any of the packages to the latest version, you might upgrade graphviz 
Install nesc
sudo dpkg -i nesc_1.1.2b-2_i386.deb 
Having completed the above we also need to do the following:

To use java code I had to change the 
/opt/tinyos-1.x/tools/java/Makefile.include 
to use the IBM javac rather than the sun 1.5 version
JAVAC = /opt/IBMJava2-142/bin/javac
cd $TOSROOT/tools/java; make
To change the version of java used run the following command:
sudo update-alternatives --config java
To change javac run
sudo update-alternatives --config javac
For some reason the libgetenv.so isn't being installed properly so do a manual copy:
sudo cp libgetenv.so /opt/IBMJava2-142/jre/bin/
sudo cp libgetenv.so /opt/IBMJava2-142/jre/


Then to run the java applications we need to specify the IBM jre
/opt/IBMJava2-142/bin/java net.tinyos.sf.SerialForwarder
Also we need to map the /dev/USB1 to /dev/ttyS3 for using serialforwarder et al. NB we use USB0 for the programming USB1 for serialforwarder. This is correct.
sudo mv /dev/ttyS3 /dev/ttyS3.bak
sudo ln -s /dev/ttyUSB1 /dev/ttyS3
sudo chmod 666 /dev/ttyS*
Need to add the following CLASSPATHs to compile code:
 export CLASSPATH=$CLASSPATH\:/home/mgilroy/repository/java/:/home/mgilroy/mysql_odbc/mysql-connector-java-5.0.6/mysql-connector-java-5.0.6-bin.jar

Should be able to complie using:
make micaz install mib510,/dev/ttyUSB0

Insert the following code into a file called .bash_tinyos

# Copyright (c) 2006 Chad Metcalf <chad@5secondfuse.com> 
#
# Permission is hereby granted, free of charge, to any person obtaining
# a copy of this software and associated documentation files (the
# "Software"), to deal in the Software without restriction, including
# without limitation the rights to use, copy, modify, merge, publish,
# distribute, sublicense, and/or sell copies of the Software, and to
# permit persons to whom the Software is furnished to do so, subject to
# the following conditions:
#
# The above copyright notice and this permission notice shall be 
# included in all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
# NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS
# BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN
# ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
# CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

# Java 
#export JDKROOT=/usr/lib/jvm/java-1.5.0-sun 
export JDKROOT=/opt/IBMJava2-142 
export JAVAXROOT=$JDKROOT 

export PATH="/usr/local/bin:/opt/IBMJava2-142/bin:$PATH" 

# Ubuntu 6.10 comes with gcc 4.1 which is currently broken with TOSSIM so we'll
# use gcc/g++ 4.0
export CC=gcc-4.0
export CXX=g++-4.0

# Set your default version of TinyOS here.
if [ "$TINYOS_VER" == "" ]; then
        export TINYOS_VER=2
        export BOOMERANG=0
fi

# Preserve any non Tinyos related class paths that have been set prior 
# to this file being sourced. We check the for an empty OLD_CLASSPATH
# to ensure that OLD_CLASSPATH only gets set once. 
if [ "$OLD_CLASSPATH" == "" ]; then
        if [ "$CLASSPATH" == "" ]; then
                export OLD_CLASSPATH="empty"
        else
                export OLD_CLASSPATH=$CLASSPATH
        fi
fi

# Conditional environmental setup for 3 versions of TinyOS
if [ "$TINYOS_VER" == "1" ]; then

    export TOSROOT=/opt/tinyos-1.x
    export TOSDIR=$TOSROOT/tos
    export MAKERULES=$TOSROOT/tools/make/Makerules
        
    unset CLASSPATH

        # Restore the old non tinyos classpath if its not empty
        if [ "$OLD_CLASSPATH" != "empty" ]; then
                export CLASSPATH=$OLD_CLASSPATH
        fi

        export CLASSPATH=$CLASSPATH\:`$TOSROOT/tools/java/javapath`

        if [ "$BOOMERANG" == "1" ]; then

                echo "Setting up for TinyOS 1.x with Boomerang"
                export MOTEIV_DIR=/opt/moteiv
                export TOSMAKE_PATH=$MOTEIV_DIR/tools/make
                for a in $MOTEIV_DIR/tools/java/jars/* $MOTEIV_DIR/tools/java
                do
                    export MOTEIV_CLASSPATH="$a:$MOTEIV_CLASSPATH"
                done
                
                export CLASSPATH=$MOTEIV_CLASSPATH\:$MOTEIV_DIR/tools/java\:$CLASSPATH  

                # help build files in $TOSDIR/../tools/java/net/tinyos
                export MIGFLAGS="-target=telosb -I$TOSDIR/lib/CC2420Radio"
                export SURGE_PLATFORM=telos     

        else

                echo "Setting up for TinyOS 1.x"

        fi

        # These aliases only apply to a 1.x environment
    alias tinyviz="$TOSROOT/tools/java/net/tinyos/sim/tinyviz"
        alias Deluge="java net.tinyos.tools.Deluge"

else

    echo "Setting up for TinyOS 2.x"
    export TOSROOT=/opt/tinyos-2.x
    export TOSDIR=$TOSROOT/tos
        
        unset CLASSPATH

        # Restore the old non tinyos classpath if its not empty
        if [ "$OLD_CLASSPATH" != "empty" ]; then
                export CLASSPATH=$OLD_CLASSPATH
        fi

    export CLASSPATH=$CLASSPATH\:$TOSROOT/support/sdk/java/tinyos.jar\:$TOSROOT/support/sdk/java/

    export PYTHONPATH=:$TOSROOT/support/sdk/python/
    export MAKERULES=$TOSROOT/support/make/Makerules
    unset TOSMAKE_PATH

fi

# Finally set the path for the new MSPGCCROOT
export MSPGCCROOT=/opt/msp430
export PATH="$MSPGCCROOT/bin:$PATH"

# Helpful aliases 
alias sf="java net.tinyos.sf.SerialForwarder"
alias listen="java net.tinyos.tools.Listen"

alias apps="cd $TOSROOT/apps"
alias tos="cd $TOSROOT/tos"

# Environment changing functions

# Change this shell's environment to support Tinyos 2.x development
function tos2 () {
        export TINYOS_VER=2
        export BOOMERANG=0
        . ~/.bash_tinyos
}

# Change this shell's environment to support Tinyos 1.x development
function tos1 () {
        export TINYOS_VER=1
        export BOOMERANG=0
        . ~/.bash_tinyos
}

# Change this shell's environment to support Boomerang
function boomerang () {
        export TINYOS_VER=1
        export BOOMERANG=1
        . ~/.bash_tinyos
}

# Set the MOTECOM variable to the first mote in motelist
function setMoteCom () {
    MOTE=`motelist -c| cut -d, -f2`

    if [ "$BOOMERANG" == "1" ]; then
        TYPE="tmote"
    else
        TYPE="telosb"
    fi
    
    export MOTECOM="serial@$MOTE:$TYPE"
}

# Change ownership of the TinyOS directories to the TinyOS group. This
# was originally written for the LiveCD xubuntos but it's handy to have
# around.
function tos-fix-permissions () {
    echo "sudo may prompt you for your password."
    sudo chown -R root:tinyos /opt/tinyos-*
    sudo chmod -R g+w /opt/tinyos-*
    sudo find /opt/tinyos-* -type d -exec chmod 2775 {} \;
}

---

### Post by newsman on 2007-06-28
yeah i was having problems with the old install some time ago,, the new installation worked like a charm. i hope they just keep updating xubunTOS (linke on top of 5secondfuse.com) at the moment i think thier live cd does not allow dual operating system (last time i checked)

---

