---
title: "Firestorm won't run on Ubuntu 13.10"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by maggie3 on 2014-04-02
I am new to Ubuntu and Linix, and have been having a great deal of difficulty either running or installing Firestorm for Second Life.  I am running 64-bit Ubuntu 13.10, and am trying to run the 64-bit version of Firestorm.  

STEP 1:
I downloaded Firestorm for SL or OpenSim 64-bit at this location:  [http://www.firestormviewer.org/downloads/](http://www.firestormviewer.org/downloads/), selecting the Linix tab.  I extracted the folder and its contents into the Home directory.

STEP 2:
Using Terminal, I viewed the folder contents, and they are shown below:

maggie@Pavilion-dv7:~/Firestorm$ ls
app_settings
bin
character
etc
featuretable_linux.txt
firestorm
firestorm_48.png
FIRESTORM_DESKTOPINSTALL.txt
firestorm_icon.png
fonts
fs_resources
gpu_table.txt
install.sh
lib
licenses.txt
Phoenix_FirestormOS-Beta_x86_64_4.6.1.40478
Phoenix_FirestormOS-Beta_x86_64_4.6.1.40478.tar.bz2
README-linux-joystick.txt
README-linux.txt
README-linux-voice.txt
res-sdl
secondlife-i686.supp
skins
summary.json
VivoxAUP.txt
maggie@Pavilion-dv7:~/Firestorm$ 

STEP 3:

The Readme-linux.txt file contains the following instructions:

INSTALLING & RUNNING
-=-=-=-=-=-=-=-=-=-=-=-

The Firestorm Linux client can entirely run from the directory you have
unpacked it into - no installation step is required.  If you wish to
perform a separate installation step anyway, you may run './install.sh'

Run './firestorm' from the installation directory to start Firestorm.

STEP 4:

I attempted to follow these instructions and run the program in terminal.  I got the following error:

maggie@Pavilion-dv7:~/Firestorm$ ./firestorm
64-bit Linux detected.
Running from /home/maggie/Firestorm
./firestorm: line 99: ./etc/register_hopprotocol.sh: No such file or directory
./firestorm: line 100: ./etc/register_secondlifeprotocol.sh: Permission denied
./firestorm: line 160: bin/do-not-directly-run-firestorm-bin: Permission denied
*** Bad shutdown ($LL_RUN_ERR). ***

You are running the Firestorm Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-firestorm-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
maggie@Pavilion-dv7:~/Firestorm$ 

STEP 5:

I noticed the permission denied part of the error, and wondered if it is necessary to use the sudo command.  I tried the command again using sudo:

maggie@Pavilion-dv7:~/Firestorm$ sudo ./firestorm
[sudo] password for maggie: 
64-bit Linux detected.
Running from /home/maggie/Firestorm
./firestorm: line 99: ./etc/register_hopprotocol.sh: No such file or directory
./firestorm: line 100: ./etc/register_secondlifeprotocol.sh: Permission denied
./firestorm: line 160: bin/do-not-directly-run-firestorm-bin: Permission denied
*** Bad shutdown ($LL_RUN_ERR). ***

You are running the Firestorm Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-firestorm-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
maggie@Pavilion-dv7:~/Firestorm$ 

STEP 6:
Now I am baffled, because it is 64-bit Firestorm that I am trying to run, and I am running it on Ubuntu 13.10 64-bit.  How can that be a problem?  I do some web searching, and I read that 13.10 has built-in 32-bit compatibility.  Now I am even more confused.  In desperation, I try installing the requested files......$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl.  Some of them install okay, some are not found but suggest replacements, and I install the replacements that are available.

STEP 7:
I try again.......no change........exact same results in the terminal window.

CONCLUSION:
I must be completely missing the problem, or trying to solve it wrong.  I am troubled by the error messages on line 99, 100, and 160, but don't have a clue what it means or how to fix it.  Can anyone tell me what is wrong?

Maggie

---

### Post by su:bhatta on 2014-04-03
> 
The Firestorm Linux client can entirely run from the directory you have
unpacked it into - no installation step is required.

First, extract the contents into a Folder.

You have to just run the Executable file 'firestorm' by double clicking on it.
See if that works.
As the Readme says, you Don't have to do ./firestorm.


Also, please do not open new thread for same problems, just put a 'bump' in the old post, which didn't get any response 
That way the old post will come up front and you will see new responses :)

---

### Post by sandyd on 2014-04-03
<wrong thread, ignore me...>
* gulps down a coffee

---

### Post by 23dornot23d on 2014-04-03
It seems it never got unpacked ......



Could run

[SIZE=5][B]cd /home/maggie/Firestorm

./install.sh[/B][/SIZE]

then

[SIZE=5]**./firestorm**[/SIZE]

see if that works ...... but the main errors you were getting are that no files were there to execute or to use for the program.

or if you are not keem on a full install - just check this file out ........ below 

[ It looks as if this file never got un-compressed ..... [COLOR=#ff0000]**Phoenix_FirestormOS-Beta_x86_64_4.6.1.40478.tar.bz2**[/COLOR] - usually a double click on it will show
what files are held within it - just to have a quick check to see what is there ..... or run a archive program to look at it ]

My own thoughts are if it runs ok from being unpacked then there is no need for a full install ..... ( not got the time to check it out at the moment - but may look again later at this )

Would maybe try it from a flash drive or something first .... but not using sudo ..... or giving it priveleges to install into your system ..... games are just distractions.

---

### Post by maggie3 on 2014-04-03
bhattabhishek,

Thanks for your comments, and I will try your suggestion about using a reply to bump up the old post; however, since this is a different section of the forum, I had thought it would be more helpful to post here.

With regard to extracting the downloaded program, I completed that in the first step that I described above.  With regard to double clicking on the file named "firestorm", I opened the file manager, and doubled clicked on the file, and it opened a window that displayed the contents listed below.  I am not sure what the window really is........it looks like a file manager window, but it seems to be displaying the text of the file contents.  Anyway, here are the contents that it displayed:

#!/bin/bash

## Here are some configuration options for Linux Client Testers.
## These options are for self-assisted troubleshooting during this beta
## testing phase; you should not usually need to touch them.

## AO: TCMALLOC Tuning as suggested by Henri Beauchamp for more aggressive garbage collection
export TCMALLOC_RELEASE_RATE=10000

## - Avoids using any FMOD Ex audio driver.
#export LL_BAD_FMODEX_DRIVER=x

## - Avoids using any OpenAL audio driver.
#export LL_BAD_OPENAL_DRIVER=x

## - Avoids using the FMOD Ex PulseAudio audio driver.
#export LL_BAD_FMOD_PULSEAUDIO=x
## - Avoids using the FMOD or FMOD Ex ALSA audio driver.
#export LL_BAD_FMOD_ALSA=x
## - Avoids using the FMOD or FMOD Ex OSS audio driver.
#export LL_BAD_FMOD_OSS=x

## - Avoids the optional OpenGL extensions which have proven most problematic
##   on some hardware.  Disabling this option may cause BETTER PERFORMANCE but
##   may also cause CRASHES and hangs on some unstable combinations of drivers
##   and hardware.
## NOTE: This is now disabled by default.
#export LL_GL_BASICEXT=x

## - Avoids *all* optional OpenGL extensions.  This is the safest and least-
##   exciting option.  Enable this if you experience stability issues, and
##   report whether it helps in the Linux Client Testers forum.
#export LL_GL_NOEXT=x

## - For advanced troubleshooters, this lets you disable specific GL
##   extensions, each of which is represented by a letter a-o.  If you can
##   narrow down a stability problem on your system to just one or two
##   extensions then please post details of your hardware (and drivers) to
##   the Linux Client Testers forum along with the minimal
##   LL_GL_BLACKLIST which solves your problems.
#export LL_GL_BLACKLIST=abcdefghijklmno

## - Some ATI/Radeon users report random X server crashes when the mouse
##   cursor changes shape.  If you suspect that you are a victim of this
##   driver bug, try enabling this option and report whether it helps:
#export LL_ATI_MOUSE_CURSOR_BUG=x

if [ "`uname -m`" = "x86_64" ]; then
    echo '64-bit Linux detected.'
fi


## Everything below this line is just for advanced troubleshooters.
##-------------------------------------------------------------------

## - For advanced debugging cases, you can run the viewer under the
##   control of another program, such as strace, gdb, or valgrind.  If
##   you're building your own viewer, bear in mind that the executable
##   in the bin directory will be stripped: you should replace it with
##   an unstripped binary before you run.
#export LL_WRAPPER='gdb --args'
#export LL_WRAPPER='valgrind --smc-check=all --error-limit=no --log-file=secondlife.vg --leak-check=full --suppressions=/usr/lib/valgrind/glibc-2.5.supp --suppressions=secondlife-i686.supp'

## - Avoids an often-buggy X feature that doesn't really benefit us anyway.
export SDL_VIDEO_X11_DGAMOUSE=0

## - Works around a problem with misconfigured 64-bit systems not finding GL
I386_MULTIARCH="$(dpkg-architecture -ai386 -qDEB_HOST_MULTIARCH 2>/dev/null)"
MULTIARCH_ERR=$?
if [ $MULTIARCH_ERR -eq 0 ]; then
    echo 'Multi-arch support detected.'
    MULTIARCH_GL_DRIVERS="/usr/lib/${I386_MULTIARCH}/dri"
    export LIBGL_DRIVERS_PATH="${LIBGL_DRIVERS_PATH}:${MULTIARCH_GL_DRIVERS}:/usr/lib64/dri:/usr/lib32/dri:/usr/lib/dri"
else
    export LIBGL_DRIVERS_PATH="${LIBGL_DRIVERS_PATH}:/usr/lib64/dri:/usr/lib32/dri:/usr/lib/dri"
fi

## - The 'scim' GTK IM module widely crashes the viewer.  Avoid it.
if [ "$GTK_IM_MODULE" = "scim" ]; then
    export GTK_IM_MODULE=xim
fi

## - Automatically work around the ATI mouse cursor crash bug:
## (this workaround is disabled as most fglrx users do not see the bug)
#if lsmod | grep fglrx &>/dev/null ; then
#    export LL_ATI_MOUSE_CURSOR_BUG=x
#fi


## Nothing worth editing below this line.
##-------------------------------------------------------------------

SCRIPTSRC=`readlink -f "$0" || echo "$0"`
RUN_PATH=`dirname "${SCRIPTSRC}" || echo .`
echo "Running from ${RUN_PATH}"
cd "${RUN_PATH}"

# Re-register hop:// and secondlife:// protocol handler every launch, for now.
./etc/register_hopprotocol.sh
./etc/register_secondlifeprotocol.sh

# Re-register the application with the desktop system every launch, for now.
# AO: Disabled don't install by default
#./etc/refresh_desktop_app_entry.sh

## Before we mess with LD_LIBRARY_PATH, save the old one to restore for
##  subprocesses that care.
export SAVED_LD_LIBRARY_PATH="${LD_LIBRARY_PATH}"

# if [ -n "$LL_TCMALLOC" ]; then
#    tcmalloc_libs='/usr/lib/libtcmalloc.so.0 /usr/lib/libstacktrace.so.0 /lib/libpthread.so.0'
#    all=1
#    for f in $tcmalloc_libs; do
#        if [ ! -f $f ]; then
#        all=0
#    fi
#    done
#    if [ $all != 1 ]; then
#        echo 'Cannot use tcmalloc libraries: components missing' 1>&2
#    else
#    export LD_PRELOAD=$(echo $tcmalloc_libs | tr ' ' :)
#    if [ -z "$HEAPCHECK" -a -z "$HEAPPROFILE" ]; then
#        export HEAPCHECK=${HEAPCHECK:-normal}
#    fi
#    fi
#fi

export LD_LIBRARY_PATH="$PWD/lib:${LD_LIBRARY_PATH}"
# AO: experimentally removing to allow --settings on the command line w/o error. FIRE-1031
#export SL_OPT="`cat etc/gridargs.dat` $@"

# <FS:ND> [blerg] set LD_PRELOAD so plugins will pick up the correct sll libs, otherwise they will pick up the system versions.
LLCRYPTO="`pwd`/lib/libcrypto.so.1.0.0"
LLSSL="`pwd`/lib/libssl.so.1.0.0"
if [ -f ${LLCRYPTO} ]
then
    export LD_PRELOAD="${LD_PRELOAD}:${LLCRYPTO}"
fi
if [ -f ${LLSSL} ]
then
    export LD_PRELOAD="${LD_PRELOAD}:${LLSSL}"
fi
# <FS:ND> End of hack; God will kill a kitten for this :(


# Copy "$@" to ARGS array specifically to delete the --skip-gridargs switch.
# The gridargs.dat file is no more, but we still want to avoid breaking
# scripts that invoke this one with --skip-gridargs.
ARGS=()
for ARG in "$@"; do
    if [ "--skip-gridargs" != "$ARG" ]; then
        ARGS[${#ARGS
[*]}]="$ARG"
    fi
done

# Run the program.
# Don't quote $LL_WRAPPER because, if empty, it should simply vanish from the
# command line. But DO quote "${ARGS[@]}": preserve separate args as
# individually quoted.
$LL_WRAPPER bin/do-not-directly-run-firestorm-bin "${ARGS[@]}"
LL_RUN_ERR=$?

# Handle any resulting errors
if [ $LL_RUN_ERR -ne 0 ]; then
    # generic error running the binary
    echo '*** Bad shutdown ($LL_RUN_ERR). ***'
    if [ "$(uname -m)" = "x86_64" ]; then
        echo
        cat << EOFMARKER
You are running the Firestorm Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-firestorm-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
EOFMARKER
    fi
fi

---

### Post by maggie3 on 2014-04-03
bhattabhishek,

I later discovered that the window that opened when I double clicked on "firestorm" was a gedit window.  I presume this means double clicking opened it for editing rather than to run it.  I notice that when I right-click on the file "firestorm", it offers me the choice to open it with gedit or with some other program.........as though firestorm were not a program itself.

---

### Post by deadflowr on 2014-04-03
> **maggie3 said:**
> bhattabhishek,

I later discovered that the window that opened when I double clicked on "firestorm" was a gedit window.  I presume this means double clicking opened it for editing rather than to run it.  I notice that when I right-click on the file "firestorm", it offers me the choice to open it with gedit or with some other program.........as though firestorm were not a program itself.

This is what many consider a bug with the file management of Ubuntu.
executables are set to view instead of either ask, or run.
To change it open the Files program and then go to Edit > Preferences.
Go to Behavior and look for the executables section.
Change it from view to either of the other options.
Then close.
This should allow you to double click to run, or at least ask you to run, instead of opening gedit.

Hope this helps.
Or makes sense...

---

### Post by su:bhatta on 2014-04-04
^^^ +1

maggie3, deadflowr has given a generic way to make sure that any executable file is 'run' by default and not open in gedit.

Another thing you can try is to select the file Firestorm and right click on it, under Properties you will find Permissions, and make sure 'Is Executable' box is checked .
Then try to double click and run Firestorm.

---

### Post by maggie3 on 2014-04-04
23dornot23d,

Thanks for your suggestions.  Your comments got me looking back at my own post more carefully - and I have gotten it working as a result.  Thanks!

---

