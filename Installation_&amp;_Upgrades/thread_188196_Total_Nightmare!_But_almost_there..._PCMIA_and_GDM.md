---
title: "Total Nightmare! But almost there... PCMIA and GDM not working"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2006-06-03
Okay, it all started with me just changing the name to dapper in my sources and doing a dist upgrade.... 120+ packages were broken. All day long I babysat synaptic while I played with stuff until I got all 600+mb of packages installed....

I reboot my computer and X wouldn't come up, it refused to see my video card and PCMIA services were not starting.

I eventually got X to work again by dpkg-reconfigure xserver-org then manually going in and changing the xorg.conf file to point to my nvidia driver... this would not work unless I stopped gdm first (even though x woouldn't start, apparently gdm was running in the background).... it was very scary and frustrating to be stuck in the console for so long. I had to use lynx to come read this site....

anyway... problems

Starting PCMCIA Services .... [FAILED]

^ I get that during boot that can NOT be good

then no matter what I seem to do the GDM does not seem to work. It says 'there is an error in the config, running default login' or some similiar jargon... i tried dpkg-reconfigure gdm and restarting, but it did nothing to help. I tried changing the theme in system->administration->login window and that did nothing either.

Any help? I've been at this all day, it's very frustrating and I regret upgrading.

---

### Post by psb6m on 2006-06-03
I had something like this; maybe it's the same. Boot into recovery mode, and while in that mode upgrade to the latest version of the kernel (upgrading for some reason doesn't automatically upgrade that). Then reboot. I bet PCMCIA will be back.

---

### Post by skelooth on 2006-06-03
as far as I know I do have the most recent kernel (I think 2.6? I forget how to check and don't want to restart to look at grub lol.)

---

### Post by psb6m on 2006-06-03
run uname -r: it should be 2.6.15-23-686.

---

### Post by skelooth on 2006-06-03
root@l337-Machine:/etc # uname -r
2.6.15-23-386

?? are the last three numbers just the architecture?

---

### Post by skelooth on 2006-06-03
*pulls hair out*

I tried installing anything i could find in synaptic that said pcmcia, then i tried to regonfigure gdm one last time...

but i still get those same two errors :( The computer is usable but I do not like error messages.... they do not lead to good things. Any other ideas would be great. Apparently pcmcia, x, and gdm problems are common with the upgrade

---

### Post by psb6m on 2006-06-03
You have the latest kernel;  but assuming you're running a Pentium III or better you should intall and use the 686 kernel.

Oh, but the PCMCIA problem. Sorry, I'm out of ideas. But it's nice that your system is usable. Mine wasn't, till I had figured out what was wrong.

---

### Post by skelooth on 2006-06-03
okay, since pcmcia is only used by laptops anyway (?right?) I'm not too worried about that....  

I'm running an AMD Duron 1800, oldschool. I'm not sure if that 'qualifies' as pentium3 class or not? it runs at 1.1ghz and i have 1gig ram

NEW PROBLEM!!!!!!!!!!!! jar ufm manifest.txt myjar.jar is not working all of a sudden.... it jars w/o any errors, inserts the manifest file w/ no errors, but when i try to run it with java -jar myjar.jar it acts like either myjar.jar doesn't exist or it has no manifest file...

```
skel1@l337-Machine:~/Desktop/javastuff/game$ java -jar /home/skel1/Desktop/javastuff/game/myjar.jar
Failed to load Main-Class manifest attribute from /home/skel1/Desktop/javastuff/game/myjar.jar

```

This is very upsetting because I've been working on this engine for 2 or three weeks. The old backed up jars still work fine, it still compiles fine, but suddenly i can not jar them??? And I've changed nothing other than what was done through synaptic. (I manually installed my JDK)

---

### Post by hod139 on 2006-06-03
Make sure you have the ubuntu-desktop package installed.  Hopefully that will fix some of the X issues.

For java, there are now official sun packages available in the repos.  I made an [eariler post]("http://ubuntuforums.org/showpost.php?p=1065271&postcount=8") about how to set up eclipse and sun's java that may be useful to you.

---

### Post by skelooth on 2006-06-03
ahh, for some reason dapper pasted symbolic links to the 1.4 jre on top of mine.... why would dapper install an outdated jre? There's no need for java being in the repos, it's very simple to sit up. Just install and make some symbolic links in /usr/bin

that was close....

now just gotta fix gdm

---

### Post by ubuntu_demon on 2006-06-04
WARNING / take a look here prior to upgrading and installing!
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)
> 
During dist-upgrading from Breezy to Dapper non-official repos should be commented. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically.


Here are some fixes :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by skelooth on 2006-06-04
no offense, but I fail to see the helpfulness of linking me to the sticky. It was probably the first thing I read. The only thing still broken at this point is PCMCIA Services Failing at boot, and GDM not working correctly

---

### Post by Nordoelum on 2006-06-04
[quote=hod139]Make sure you have the ubuntu-desktop package installed.  Hopefully that will fix some of the X issues.

For java, there are now official sun packages available in the repos.  I made an [eariler post]("http://ubuntuforums.org/showpost.php?p=1065271&postcount=8") about how to set up eclipse and sun's java that may be useful to you.[/quote] So I need both xubuntu-desktop and ubuntu-desktop?

[QUOTE=skelooth]no offense, but I fail to see the helpfulness of linking me to the sticky. It was probably the first thing I read. The only thing still broken at this point is PCMCIA Services Failing at boot, and GDM not working correctly[/QUOTE]I know. I did the sticky, but it didn't help me.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=skelooth]no offense, but I fail to see the helpfulness of linking me to the sticky. It was probably the first thing I read. The only thing still broken at this point is PCMCIA Services Failing at boot, and GDM not working correctly[/QUOTE]
The stickies get updated over time. So they might help you.

Did you try the "HOWTO fix problems regarding broken dependencies" :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
in order to make sure there are no broken dependencies left ?

You can use sysv-rc-conf to turn off pcmcia.
Here's some explanation about it : [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
$sudo apt-get install sysv-rc-conf
$sudo sysv-rc-conf

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Nordoelum]So I need both xubuntu-desktop and ubuntu-desktop?

I know. I did the sticky, but it didn't help me.[/QUOTE]
No you can choose between :
kubuntu-destop, edubuntu-destop,xubuntu-destop and ubuntu-destop

But it is possible to install them together if you want.

---

### Post by skelooth on 2006-06-04
Yeah, I fixed most of my problems by just hacking around on my own... This upgrade has been plagued with problems. Thank god for lynx, nano, and man.

Anyway, i installed ubuntu-desktop package, installed my nvidia drivers, dpkg-reconfigure gdm then restarted.... it did nothing. Unfortunately it won't let me copy paste the error but it's something like

"the config file contains an invalid command, using default login"

---

### Post by skelooth on 2006-06-04
yes, i did :p

But all that does is turn off something that used to work. That's like using the microwave to toast your bread because the toaster is broken....

I'm kinda lost on what might be wrong in the GDM config... ? and... which one?  is it complaining about /etc/gdm/gdm.conf? I can only guess it is, and the file looks fine

---

### Post by ubuntu_demon on 2006-06-04
If you don't have a laptop you probably won't have pcmcia at all it's perfectly possible that this results in a fail during booting. If you do have a laptop you might get pcmcia working if you are lucky and otherwise file bug reports, sit back and hope you will get better laptop support in Edgy.

Did you edit your /etc/gdm/gdm.conf for example to get XGL working or something ?

Anyway what you should do is follow my guide from the beginning and report any errors when you get stuck :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

In your case I would advice to also do this command while following my guide :
$sudo apt-get remove xserver-xorg x-window-system-core gdm -f --purge

After you have finished the guide do a reboot and if you are still having problems with getting into X then first take a look here :

Dealing with problems with the Xserver
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

If that doesn't help you should post your :
/var/log/Xorg.0.log and /etc/gdm/gdm.conf

---

### Post by Nordoelum on 2006-06-04
@ubuntu_demon: You must fix the link to the "Or use this clean Dapper sources.list [http://www.ubuntuforums.org/showpost...38&postcount=2]("http://www.ubuntuforums.org/showpost...38&postcount=2")". You have copied the shrinked adress.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Nordoelum]@ubuntu_demon: You must fix the link to the "Or use this clean Dapper sources.list [http://www.ubuntuforums.org/showpost...38&postcount=2]("http://www.ubuntuforums.org/showpost...38&postcount=2")". You have copied the shrinked adress.[/QUOTE]
thnx!
and done :)

---

### Post by skelooth on 2006-06-04
gdm.conf
```
# GDM Configuration file.  You can use gdmsetup program to graphically
# edit this, or you can optionally just edit this file by hand.  Note that
# gdmsetup does not tweak every option here, just the ones most users
# would care about.  Rest is for special setups and distro specific
# tweaks.  If you edit this file, you should run:
# /etc/init.d/gdm reload or /etc/init.d/gdm restart

# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form
# on http://www.jirka.org/gdm.html
#
# NOTE: Some of these are commented out but still show their default values.
# If you wish to change them you must remove the '#' from the beginning of
# the line.  The commented out lines are lines where the default might
# change in the future, so set them one way or another if you feel
# strongly about it.
#
# Have fun! - George

[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/bin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/bin/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/bin/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/bin/gdmlogin

# Launch the greeter with an additional list of colon seperated gtk 
# modules. This is useful for enabling additional feature support 
# e.g. gnome accessibility framework. Only "trusted" modules should
# be allowed to minimise security holes
#AddGtkModules=false
# By default these are the accessibility modules
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and
# want gdm to kill/restart the server, turn this on
#AlwaysRestartServer=false

# User and group used for running gdm GUI applicaitons.  By default this
# is set to user gdm and group gdm.  This user/group should have very
# limited permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# doesn't always work, only if those clients have a window of their own
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup
PidFile=/var/run/gdm.pid
# Note that a post login script is run before a PreSession script.
# It is run after the login is successful and before any setup is
# run on behalf of the user
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say
# VGA mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can
# run an X configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal
# X session, but it shares a lot of stuff with that.  See the provided
# default for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live
# It is really a PATH style variable since 2.4.4.2 to allow actual
# interoperability with KDM.  Note that <sysconfdir>/dm/Sessions is there
# for backwards compatibility reasons with 2.4.4.x
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this behaviour.
UserAuthDir=
# Fallback if home directory not writable
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/X11R6/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is
# no activity and no one logged on.  Set to 0 to turn off the reaping.
# Does not affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# the X nest command
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way
# we force X to use specific vts.  turn VTAllocation to false if this
# is causing problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change
# vts on linux and freebsd systems for console logins)
#DoubleLoginWarning=true

# If true then the last login information is printed to the user before
# being prompted for password.  While this gives away some info on what
# users are on a system, it on the other hand should give the user an
# idea of when they logged in and if it doesn't seem kosher to them,
# they can just abort the login and contact the sysadmin (avoids running
# malicious startup scripts)
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used
# when there are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

[security]
# If any distributions ship with this one off, they should be shot
# this is only local, so it's only for say kiosk use, when you
# want to minimize possibility of breakin
AllowRoot=false
# If you want to be paranoid, turn this one off
AllowRemoteRoot=false
# This will allow remote timed login
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a bad login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line,
# a good default to have (why is this a "negative" setting? because if
# it is false, you could still not allow it by setting command line of
# any particular server).  It's probably better to ship with this on
# since most users will not need this and it's more of a security risk
# then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do
# not add a "-nolisten tcp", as then the query just wouldn't work, so
# this setting only affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS
# by detecting "root-squashing".  It seems bad practice to place
# cookies on things that go over the network by default and thus we
# don't do it by default.  Sometimes you can however use safe remote
# filesystems where this is OK and you may want to have the cookie in your
# home directory.
#NeverPlaceCookiesOnNFS=true

# XDMCP is the protocol that allows remote login.  If you want to log into
# gdm remotely (I'd never turn this on on open network, use ssh for such
# remote usage that).  You can then run X with -query <thishost> to log in,
# or -indirect <thishost> to run a chooser.  Look for the 'Terminal' server
# type at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false
# Honour indirect queries, we run a chooser for these, and then redirect
# the user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time
#MaxSessions=16
# Maximum wait times
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single
# host.  This is now set at 2 since if the server crashes then gdm doesn't
# know for some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way
#Port=177
# Willing script, none is shipped and by default we'll send
# hostname system id.  But if you supply something here, the
# output of this script will be sent as status of this host so that
# the chooser can display it.  You could for example send load,
# or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc
# that we need.  Unless you need a specific gtkrc that doesn't correspond to
# a specific theme, then just use the GtkTheme key
#GtkRC=/usr/share/themes/Default/gtk/gtkrc

# The GTK+ theme to use for the gui
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does
# not yet have this ability
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can
# also specify 'all' to allow all installed themes.  These should be just
# the basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# Greeter has a nice title bar that the user can move
#TitleBar=true
# Configuration is available from the system menu of the greeter
ConfigAvailable=false
# Face browser is enabled.  This only works currently for the
# standard greeter as it is not yet enabled in the graphical greeter.
Browser=false
# The default picture in the browser
#DefaultFace=/usr/share/pixmaps/nobody.png
# These are things excluded from the face browser, not from logging in
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# As an alternative to the above this is the minimum uid to show
MinimalUID=1000
# If user or user.png exists in this dir it will be used as his picture
#GlobalFaceDir=/usr/share/faces/
# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with gdm and edit it.  It is not a standard locale.alias file,
# although gdm will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter
#Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true
# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however
SystemMenu=true
# The Actions in the Actions menu require the root password
SecureSystemMenu=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user
# to connect to some remote host.  Local XDMCP does not need to be enabled
# however
#ChooserButton=true
# Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# Welcome[cs]=Vitejte na %n
# Just make sure the string is in utf-8
# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# The default entries that are shipped are translated inside gdm and
# are as follows:
#Welcome=Welcome
#RemoteWelcome=Welcome to %n
# Don't allow user to move the standard greeter window.  Only makes sense
# if TitleBar is on
#LockPosition=false
# Set a position rather then just centering the window.  If you enter
# negative values for the position it is taken as an offset from the
# right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0
# Xinerama screen we use to display the greeter on.  Not for true
# multihead, currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image, 2=Color
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
BackgroundColor=#523921
# XDMCP session should only get a color, this is the sanest setting since
# you don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true
# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# if this is true then the background program is run always, otherwise
# it is only run when the BackgroundType is 0 (None)
#RunBackgroundProgramAlways=false
# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=false
# Use circles in the password field.  Looks kind of cool actually,
# but only works with certain fonts.
UseCirclesInEntry=true
# These two keys are for the new greeter.  Circles is the standard
# shipped theme
GraphicalTheme=happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font
# to be used when displaying the contents of the file.
#InfoMsgFont=Sans 24
# If SoundOnLogin is true, then the greeter will beep when login is ready
# for user input.  If SoundOnLogin is a file and the greeter finds the
# 'play' executable (see daemon/SoundProgram) it will play that file
# instead of just beeping
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav

# The chooser is what's displayed when a user wants an indirect XDMCP
# session, or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are
# scanning actually, we continue to listen even after this has
# expired)
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to
# a query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced when
# officially registered xdmcp multicast address of TBD will be available
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names
#AllowAdd=true

[debug]
# This will enable debugging into the syslog, usually not neccessary
# and it creates a LOT of spew of random stuff to the syslog.  However it
# can be useful in determining when something is going very wrong.
Enable=false

[servers]
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost)
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look
# at the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0
flexible=true

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params
# anyway, and terminate would be bad for xdmcp choosing).  You can
# make a terminal server flexible, but not with an indirect query.
# If you need flexible indirect query server, then you must get rid
# of the -terminate and the only way to kill the flexible server will
# then be by Ctrl-Alt-Backspace
flexible=false
# Not local, we do not handle the logins for this X server
handled=false

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you
# wish to allow a chooser server then make this true.  This is the
# only way to make a flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a
# machine they will get this same server but run with
# "-terminate -query hostname"
chooser=true

```

---

### Post by skelooth on 2006-06-04
and here is the xorg.0.log



xorg.0.log
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux l337-Machine 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  4 10:54:50 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:08:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1106,4161 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1106,0102 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 5333,8d04 card 5333,8d04 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xddd00000 - 0xddefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbdc00000 - 0xcdbfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:8:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xdf000000/24, 0xd0000000/27, BIOS @ 0xdefe0000/17
(--) PCI: (1:0:0) S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xdde80000/19, 0xc0000000/27, BIOS @ 0xdde70000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[1] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[1] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[1] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[1] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[5] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:08:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[5] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[5] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:0:8:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.15.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:0:8:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdefdfe00 - 0xdefdfeff (0x100) MX[B]
	[7] -1	0	0xdefdff00 - 0xdefdffff (0x100) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[12] -1	0	0xdde70000 - 0xdde7ffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdde80000 - 0xddefffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

---

### Post by ubuntu_demon on 2006-06-04
please also reply to the rest of my suggestions when you have time :)

I'm away for a while (I don't know how long maybe for an hour, maybe for a couple of hours).

good luck! :)

---

### Post by Nordoelum on 2006-06-04
Can this error have anything witht the kernel to do? Since I have booted an outdated one.

Ed1t: @[skelooth:]("http://www.ubuntuforums.org/member.php?u=24187") Do an $sudo grub-update. Since I would guess you are booting an old kernel. It solved my problem.[URL="http://www.ubuntuforums.org/member.php?u=24187"]
[/URL]

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Nordoelum]Can this error have anything witht the kernel to do? Since I have booted an outdated one.

Ed1t: @[skelooth:]("http://www.ubuntuforums.org/member.php?u=24187") Do an $sudo grub-update. Since I would guess you are booting an old kernel. It solved my problem.[URL="http://www.ubuntuforums.org/member.php?u=24187"]
[/URL][/QUOTE]
You should always boot into the latest kernel. Especially when you are facing problems. I don't know what the problem is that you are facing. Please start a new thread about your problem(if you haven't done so already) and point me to the thread.

I'm going away for a while.

Good luck all ! :)

---

### Post by Nordoelum on 2006-06-04
I don't have any problems anymore :P

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Nordoelum]I don't have any problems anymore :P[/QUOTE]
great!

If you have any good/new fixes to problems please post them here :
[http://www.ubuntuforums.org/showthread.php?t=187659](http://www.ubuntuforums.org/showthread.php?t=187659)

---

### Post by Nordoelum on 2006-06-04
@skelooth: Have you tried my advise?

---

### Post by skelooth on 2006-06-04
no need, i've been booting into the latest kernel

I made a new topic about the gdm issue btw
[http://ubuntuforums.org/showthread.php?t=188943](http://ubuntuforums.org/showthread.php?t=188943)

---

### Post by Nordoelum on 2006-06-04
Okay. But did you follow the WHOLE guide ubuntu_deamon linked to? Because I guess that was the ting that solved my problem.

---

### Post by skelooth on 2006-06-04
I did half of it before ever reaching the guide. ALL dependencies are resolved, kernel is up to date, etc. The only things not working are pcmcia service and gdm is giving an error message

---

### Post by Nordoelum on 2006-06-04
I find it strange. Since it resolved for me. I use the 2.6.15-23 kernen, and then at all appeared to work as fine.

---

