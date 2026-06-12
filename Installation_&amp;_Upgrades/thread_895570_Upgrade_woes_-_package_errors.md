---
title: "Upgrade woes - package errors"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by rpinder on 2008-08-20
Hello,
I had an install that originally was 6.06.
I followed along the upgrade docs, on the way to get it up (ideally) to the current 8.04 lts.  I only need 'server' related packages.

I think the original app had installed some GUI components - but again I dont think they are necessary any longer.

Got it up part way up to 7.10  (via 7.04)
[I] cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
[/I]

But when try apt-get upgrade, I get package inconsistencies - that I can't seem to resolve:

[I]You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgnome2-0: Depends: libgnome2-common (>= 2.22) but 2.18.0-0ubuntu1 is installed
  libgnomeui-0: Depends: libgnomeui-common (>= 2.22) but 2.17.92-0ubuntu1 is installed
  libgnomevfs2-0: Depends: libgnomevfs2-common (>= 1:2.22) but 1:2.18.1-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.[/I]

apt-get -f install    doesnt help.

These errors seem all point to problems with gnome.  Trying to remove anything now keeps bumping back to the same 'inconsistencies' screens.

Do you know a way to either FORCE removeal of all gnome (or all gui ?) related packages ?
OR - is there another way to force upgrades for the libraries, so I can continue ?

Thanks
Rich

---

### Post by meindian523 on 2008-08-20
Um,why go through 7.04-->7.10?LTS versions automatically update to the next LTS.I think probably,you use Synaptic to find all packages which have gnome and search and destroy them.

---

### Post by rpinder on 2008-08-20
Thx for the reply

I dont have/use synaptec - would you suggest the way to do this using the command line, and apt ?  I tried removing some of the libraries referenced using remove, but the dependencies issue got in the way.

But this is exactly what I'd like to do - find the 'master' install that uses the Gnome stuff, and forcefully remove it..


The command that I'd tried to use for the upgrading is:
*sudo do-release-upgrade*

When I try to run it, it fails with some of the packages - long details below

[I]Upgrading
Done downloading            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 28253 files and directories currently installed.)
Preparing to replace libgnome2-common 2.18.0-0ubuntu1 (using .../libgnome2-common_2.22.0-0ubuntu1_all.deb) ...
Unpacking replacement libgnome2-common ...
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing /var/cache/apt/archives/libgnome2-common_2.22.0-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Preparing to replace passwd 1:4.0.18.1-9 (using .../passwd_1%3a4.0.18.2-1ubuntu2_i386.deb) ...
Unpacking replacement passwd ...
Preparing to replace adduser 3.103ubuntu1 (using .../adduser_3.105ubuntu1_all.deb) ...
Unpacking replacement adduser ...
Selecting previously deselected package libck-connector0.
Unpacking libck-connector0 (from .../libck-connector0_0.2.3-3ubuntu5_i386.deb) ...
Preparing to replace libdbus-glib-1-2 0.74-1 (using .../libdbus-glib-1-2_0.74-2_i386.deb) ...
Unpacking replacement libdbus-glib-1-2 ...
Selecting previously deselected package consolekit.
Unpacking consolekit (from .../consolekit_0.2.3-3ubuntu5_i386.deb) ...
Preparing to replace dbus 1.1.1-3ubuntu4 (using .../dbus_1.1.20-1ubuntu2_i386.deb) ...
Unpacking replacement dbus ...
Preparing to replace libattr1 1:2.4.32-1.1ubuntu1 (using .../libattr1_1%3a2.4.39-1_i386.deb) ...
Unpacking replacement libattr1 ...
Preparing to replace libacl1 2.2.42-1ubuntu1 (using .../libacl1_2.2.45-1_i386.deb) ...
Unpacking replacement libacl1 ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgnome2-common_2.22.0-0ubuntu1_all.deb

Could not install the upgrades [/I]

thx
rich

---

### Post by meindian523 on 2008-08-21
I think what you would do is delete the deb file mentioned <libgnome2-common_2.22.0-0ubuntu1_all.deb> from /var/cache/apt/archives and try reinstalling it using sudo apt-get install .......

---

