---
title: "[SOLVED] Installing Houdini 9 on Ubuntu 7.1"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by framebuffer on 2007-10-20
Hello,

I am trying to run Houdini 9 on ubuntu 7.1 but when I try to run it I get the following error:

The Houdini 9.0.747 environment has been initialized.
exec: 72: /opt/hfs9.0.747/bin/houdini-bin: not found

I confirmed that the file houdini-bin is indeed present in /opt/hfs9.0.747/bin/

The installation went fine without any errors.

Thanks.

---

### Post by meraleigh on 2007-10-27
I am also having issues getting Houdini 9.747 up and running on Ubuntu 7.10.

I have successfully installed the software, but when I try to run it I receive an error related to libgobject that cannot be found, when indeed it is there.

Mine does source (initialize) just fine, however.

If anyone has any information related to the successful implementation of this software on the latest version of Ubuntu I would greatly appreciate it.

Thanks

---

### Post by framebuffer on 2007-10-28
Hi,

I have requested people from the official sidefx forums to help. I have reinstalled Ubuntu 7.1 just to make sure this happens on a fresh install too.

[http://www.sidefx.com/index.php?option=com_forum&Itemid=172&page=viewtopic&p=47831#47831](http://www.sidefx.com/index.php?option=com_forum&Itemid=172&page=viewtopic&p=47831#47831)

fb.

---

### Post by wawarren on 2007-10-28
I saw your post on sidefx.  Not sure I can help too much since i'm using 7.04, but I can try.  

Are you using the 64 bit debian package or 32 bit?  

Also, when you navigate to opt/hfs9.0.747/bin and source "houdini_setup_bash" and do ldd houdini-bin what comes up?


edit:  Also, try to install the latest version down in the daily builds section.  I know they have a more recent version then buld 747

---

### Post by framebuffer on 2007-10-29
Hello! Here is the output from the terminal:

[FONT="Lucida Console"]manuj@KODE:/opt/hfs9.0.747$ source houdini_setup_bash 
The Houdini 9.0.747 environment has been initialized.
manuj@KODE:/opt/hfs9.0.747$ cd bin
manuj@KODE:/opt/hfs9.0.747/bin$ ldd houdini-bin 
        linux-gate.so.1 =>  (0xffffe000)
        libHoudiniAPPS3.so => /opt/hfs9.0.747/dsolib/libHoudiniAPPS3.so (0xf75fa000)
        libHoudiniAPPS2.so => /opt/hfs9.0.747/dsolib/libHoudiniAPPS2.so (0xf6fe5000)
        libHoudiniOPZ.so => /opt/hfs9.0.747/dsolib/libHoudiniOPZ.so (0xf6e24000)
        libHoudiniOP3.so => /opt/hfs9.0.747/dsolib/libHoudiniOP3.so (0xf6af4000)
        libHoudiniOP2.so => /opt/hfs9.0.747/dsolib/libHoudiniOP2.so (0xf62a6000)
        libHoudiniOP1.so => /opt/hfs9.0.747/dsolib/libHoudiniOP1.so (0xf5b5f000)
        libHoudiniSIM.so => /opt/hfs9.0.747/dsolib/libHoudiniSIM.so (0xf579f000)
        libHoudiniGEO.so => /opt/hfs9.0.747/dsolib/libHoudiniGEO.so (0xf5240000)
        libcollada_dae.so => /opt/hfs9.0.747/dsolib/libcollada_dae.so (0xf5219000)
        libcollada_dom.so => /opt/hfs9.0.747/dsolib/libcollada_dom.so (0xf4f74000)
        libcollada_LIBXMLPlugin.so => /opt/hfs9.0.747/dsolib/libcollada_LIBXMLPlugin.so (0xf4f6c000)
        libcollada_stdErrPlugin.so => /opt/hfs9.0.747/dsolib/libcollada_stdErrPlugin.so (0xf4f6a000)
        libcollada_STLDatabase.so => /opt/hfs9.0.747/dsolib/libcollada_STLDatabase.so (0xf4f60000)
        libHoudiniAPPS1.so => /opt/hfs9.0.747/dsolib/libHoudiniAPPS1.so (0xf4eb9000)
        libHoudiniDEVICE.so => /opt/hfs9.0.747/dsolib/libHoudiniDEVICE.so (0xf4eb2000)
        libHoudiniUI.so => /opt/hfs9.0.747/dsolib/libHoudiniUI.so (0xf4a91000)
        libHoudiniPRM.so => /opt/hfs9.0.747/dsolib/libHoudiniPRM.so (0xf4610000)
        libHoudiniUT.so => /opt/hfs9.0.747/dsolib/libHoudiniUT.so (0xf3cb2000)
        libpython2.5.so.1.0 => not found
        libutil.so.1 => /lib32/libutil.so.1 (0xf3c9f000)
        libboost_iostreams-gcc-mt-1_33_1.so.1.33.1 => /opt/hfs9.0.747/dsolib/libboost_iostreams-gcc-mt-1_33_1.so.1.33.1 (0xf3c97000)
        libxml++-2.6.so.2 => /opt/hfs9.0.747/dsolib/libxml++-2.6.so.2 (0xf3c79000)
        libxml2.so.2 => /opt/hfs9.0.747/dsolib/libxml2.so.2 (0xf3b64000)
        libz.so.1 => /opt/hfs9.0.747/dsolib/libz.so.1 (0xf3b50000)
        libglibmm-2.4.so.1 => /opt/hfs9.0.747/dsolib/libglibmm-2.4.so.1 (0xf3b07000)
        libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf3b03000)
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf3ac8000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf3a0a000)
        libiconv.so.2 => /opt/hfs9.0.747/dsolib/libiconv.so.2 (0xf3932000)
        libsigc-2.0.so.0 => /opt/hfs9.0.747/dsolib/libsigc-2.0.so.0 (0xf392c000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf3928000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf3910000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf388d000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf37f6000)
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf37f3000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf37e5000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf37dc000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf37d4000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf36e3000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf35ef000)
        libm.so.6 => /lib32/libm.so.6 (0xf35ca000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf35bf000)
        libc.so.6 => /lib32/libc.so.6 (0xf3475000)
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        libpython2.5.so.1.0 => not found
        librt.so.1 => /lib32/librt.so.1 (0xf3468000)
        /lib/ld-linux.so.2 (0xf7f7d000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf2ad0000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf2ace000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf2aca000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf2ac2000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf2abd000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf2ab8000)[/FONT]

Next, If i try to execute the following:

#!/bin/bash
cd /opt/hfs9.0.747/
source houdini_setup_bash
houdini

I get this:

manuj@KODE:~$ ./houdini
The Houdini 9.0.747 environment has been initialized.
/opt/hfs9.0.747/bin/houdini-bin: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

I am on a 64 bit ubuntu 7.1.

libpython2.5.so.1.0 is present in /usr/lib and /opt/hfs9.0.747/python/lib

Thanks.

---

### Post by wawarren on 2007-10-29
I think the environment variable for your python libs is commented out by default in your setup file. 

sudo gedit houdini_setup_bash and see if thats the case.    If so just remove the #'s and save it. 

Sorry I'm not able to double check what I just stated.  I'm at work using XP at the moment.

---

### Post by framebuffer on 2007-10-30
Hi!

I inspected the houdini_setup_bash file and was unable to find any reference to python libraries.

I am reproducing the file here for your convenience:

#
#   Environment setup script for Houdini.
#
#   To use this script you should "cd" to the hfs directory where this
#   script is located and "source" it into your bash shell or from your
#   .profile script.
#
#   Alternatively you may copy this script, remove the first if
#   statement and change the setting of the "HFS" variable to be
#   the location of your installed Houdini hfs directory.
#
#   Note that this script modifies your search path by inserting the
#   Houdini bin directory at the beginning. It also explicitly sets
#   the environment variable LD_LIBRARY_PATH which is used to
#   search for runtime libraries.
#
#   To run the script in quiet mode, specify the "-q" option on the
#   command line.
#
if [ ! -d houdini  -o  ! -d dsolib  -o  ! -d bin ]; then
    echo "You must cd to the Houdini installation directory before"
    echo "sourcing this script. This allows the script to determine"
    echo "the installed location."
else
    export HFS=$PWD

    #
    #  The following are some handy shortcuts:
    #
    export H=${HFS}
    export HB=${H}/bin
    export HDSO=${H}/dsolib
    export HD=${H}/demo
    export HH=${H}/houdini
    export HHC=${HH}/config
    export HT=${H}/toolkit
    export HSB=${HH}/sbin

    #
    #  The following is used as the generic /tmp path.  This is also
    # set on Windows to the temporary directory, so can be used for
    # system independent .hip files.
    #
    export TEMP=/tmp

    #
    # These environment variables are no longer supported.
    #
    export HIH=${HOME}/houdini9.0
    # HIL=${HSITE}/houdini9.0
    export HIS=$HH

    #
    # Look for java.
    #
    if [ "$JAVA_HOME" = "" ]; then
        # Check in PATH first
        d=$(which java 2>&1)
        if [ "$?" = "0" ]; then
            export JAVA_HOME=${d/\/bin*/}
        else
            for dir in /usr/local /usr/local/java2 /usr/local/java /opt /usr /usr/java2 /usr/java; do
                if [ -d $dir ]; then
                    d=$(find $dir -maxdepth 3 -path "*/bin/java" -printf "%h\n"| head -1 | sed 's/\/bin//')
                    if [ $d ]; then
                        export JAVA_HOME=$d
                        break
                    fi
                fi
            done
        fi
    fi

    if [ "$LD_LIBRARY_PATH" != "" ]; then
        LD_LIBRARY_PATH="${HDSO}:${LD_LIBRARY_PATH}"
    else
        LD_LIBRARY_PATH="${HDSO}"
    fi
    export LD_LIBRARY_PATH

    if [ "$JAVA_HOME" = "" ]; then
	PATH="${HB}:${HSB}:$PATH"
    else
	PATH="${HB}:${HSB}:${JAVA_HOME}/bin:$PATH"
    fi
    export PATH

    export HOUDINI_MAJOR_RELEASE=9
    export HOUDINI_MINOR_RELEASE=0
    export HOUDINI_BUILD_VERSION=747
    export HOUDINI_VERSION=${HOUDINI_MAJOR_RELEASE}.${HOUDINI_MINOR_RELEASE}.${HOUDINI_BUILD_VERSION}

    # Build machine related stuff
    export HOUDINI_BUILD_KERNEL="2.6.20-16-generic"
    export HOUDINI_BUILD_PLATFORM="Debian 4.0"
    export HOUDINI_BUILD_COMPILER="4.1.2"

    # This only applies for linux systems
    export HOUDINI_BUILD_LIBC="glibc 2.5"

    if [ $?prompt ]; then
	if [ "$1" != "-q" ]; then
	    echo "The Houdini ${HOUDINI_VERSION} environment has been initialized."
	fi
    fi
fi

I think more people are having this problem:
[http://www.phoronix.com/forums/showthread.php?t=5393](http://www.phoronix.com/forums/showthread.php?t=5393)

Thanks,
fb.

---

### Post by wawarren on 2007-10-30
> **framebuffer said:**
> 
manuj@KODE:~$ ./houdini
The Houdini 9.0.747 environment has been initialized.
/opt/hfs9.0.747/bin/houdini-bin: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

I am on a 64 bit ubuntu 7.1.

libpython2.5.so.1.0 is present in /usr/lib and /opt/hfs9.0.747/python/lib

Thanks.

Ok, I was mistaken about which file to gedit.  My apologies. 

```
cd /opt/hfs9.0.747/bin
sudo gedit hmaster
```

If you look, there's a script file that goes with hmaster-bin.  This is what you want to edit for accuracy purposes.  It has fairly good instructions on how to edit this file to make sure Houdini can find your python libs. 

Also, you can define an environment var in your startup script like this if you want. 

```
#!/bin/bash
export HDSO=/opt/hfs9.0.747/dsolib
cd /opt/hfs9.0.747/
source houdini_setup_bash
sudo /opt/hfs9.0.747/houdini/sbin/sesinetd
houdini
```

Sorry if thats not helpful enough.   You can always try installing Python 2.5 again.

---

### Post by framebuffer on 2007-11-05
Hello!

Thanks for the help!

The problem was solved by editing hmaster and giving the absolute path to the python library.

I replaced the line

PYTHON_LIB="libpython2.5.so.1.0"

with

PYTHON_LIB="/opt/hfs9.0.747/python/lib/libpython2.5.so.1.0"

Now it works!

---

### Post by afecelis on 2008-05-14
@framebuffer: I'm having the exact same problem with Houdini, but if I edit my hmaster file I see nothing about the python lib path. All I got in my file is this:
```
#!/bin/bash

# Initialize application environment.
APP_DIR=$(dirname $0)
source ${APP_DIR}/app_init.sh ${APP_DIR}

# Now run the requested binary.
exec $0-bin "$@"
```

Did you add the path in that file? Could you please post the contents of your hmaster file so I can use it as a guide?


regards,

Alvaro

---

### Post by framebuffer on 2008-05-20
Hello afecelis, sorry for the delay in reply.

I have just formatted my computer to upgrade to hardy, so i lost my hmaster file :(

But try adding the explicit path if its not there already. Are you sure you are looking in the right file? It was there in my hmaster file by default.

Let me know if it works otherwise we'll try something else.

fb.

---

### Post by Sean4000 on 2008-07-06
How is Houdini under hardy heron? Did it install okay? I am having a time trying to get it to work.

---

