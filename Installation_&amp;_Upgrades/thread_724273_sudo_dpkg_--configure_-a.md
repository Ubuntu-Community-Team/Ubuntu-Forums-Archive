---
title: "sudo dpkg --configure -a"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by eebamxela on 2008-03-14
I know this has been talked about many times over but no matter how many times i follow the many instructions i get no where. Ubuntu started giving me this error after i ran an update. I can't download anything through synaptic or the add/remove apps menu. I'm running Ubuntu 7.10- the Gutsy Gibbon.

I input "sudo dpkg --configure -a" (yes with the "sudo") into the terminal and i get this:

> [B]Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1[/B]

Can anyone make any sense out of this?

Thanks.

---

### Post by {BzF}~JOKesTER on 2008-03-14
Try And Go Ointo Synaptic And Under "Repositories" On The Toolbar Check All The Boxes In All The Tabs.....

---

### Post by eebamxela on 2008-03-14
Once i launch synaptic i get this error message:

> [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

When i close the error box, synaptic closes with it. I can't even click on the main synaptic window, because its grayed out.

---

### Post by {BzF}~JOKesTER on 2008-03-14
Try This:

apt-get update

sudo apt-get remove dpkg --purge

And:

sudo apt-get install dpkg

{Might Need The Disk For This}
:)

---

### Post by souneedalink on 2008-03-14
might try 
[COLOR="Green"]sudo apt-get -f install[/COLOR]

---

### Post by eebamxela on 2008-03-14
All of those things you suggested return the same error.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

---

### Post by {BzF}~JOKesTER on 2008-03-14
Try This:

[http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_alpha.deb](http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_alpha.deb)

And install It!!

---

### Post by Pumalite on 2008-03-14
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **Pumalite said:**
> sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

The Only Problem Is Is When He Runs The First Command It Gives A Fatal Error - Thats Why I'm Having Him Try And Re-install Via Download Link To The Reps.

---

### Post by eebamxela on 2008-03-14
can you post the link to the Amd64 compatible version if it is available. The one you posted says it is "Wrong Architecture (alpha)".

---

### Post by {BzF}~JOKesTER on 2008-03-14
KK,

[http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_amd64.deb](http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_amd64.deb)

---

### Post by souneedalink on 2008-03-14
looks serious!

The problem isnt with dpkg and installing dpkg for the alpha architecture probably will do more harm than good.

Likely going to have to purge some critical stuff and take a chance on reinstalling it.

Step ONE - backup everything now!

---

### Post by {BzF}~JOKesTER on 2008-03-14
And We'll Beleive You Becuase Your Bean Count Is

11??

Lol

:lolflag:

---

### Post by souneedalink on 2008-03-14
no you should believe me because I can read and see that the problem is that update-initramfs is failing which has nothing to do with dpkg...

regardless if your *bean count* is bigger than mine...

---

### Post by souneedalink on 2008-03-14
> **{BzF}~JOKesTER said:**
> 

sudo apt-get remove dpkg --purge

Have you ever tried this? If you are going to recomend it to others you should first try it yourself IMO.

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **souneedalink said:**
> no you should believe me because I can read and see that the problem is that update-initramfs is failing which has nothing to do with dpkg...

regardless if your *bean count* is bigger than mine...

Hey I Didn't Mean To Offend You - 

You Just Act All Overly Cautios.

Sorry  - lol

---

### Post by eebamxela on 2008-03-14
when i go to instal the .deb file its telling me 

[B]> only one software management tool is allowed to run at the same time.

Please close the other applications... yada yada...[/B]

I just restarted my comp, how can there be anything open?

---

### Post by {BzF}~JOKesTER on 2008-03-14
:)Open System Moniter And "End" Or "Kill" Any Proccesses Begining With "Update" Or "Synaptic"

---

### Post by eebamxela on 2008-03-14
nothing of the sort is running.

---

### Post by {BzF}~JOKesTER on 2008-03-14
Can You Run The Update Manager???:confused:

---

### Post by souneedalink on 2008-03-14
This is just like watching someone tell someone else to do something bad/dangerous...the suspense is killing me.

---

### Post by eebamxela on 2008-03-14
When i run update manager it tells me this:

> [B]Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.[/B]

Neither of those programs are on the list of processes running in the system monitor window.

WTF is going on here?

I keep getting this thing every time i do anything!

> [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

---

### Post by souneedalink on 2008-03-14
> **eebamxela said:**
> 

WTF is going on here?

ask the guy with the large bean count :lolflag:

---

### Post by {BzF}~JOKesTER on 2008-03-14
I'm Trying To Get More Info At Current - 

Try Running:

sudo apt-get clean

And:

sudo apt-get autoremove

And:

sudo apt-get autoclean

Get Back To You As Soon As I Find Out More About The Problem - Currentlly I Have 2 Other Poeple Getting The Exact Same Error Message As You Are - All Of Them Running AMD64 Bit Versions Of Ubuntu - So I'm Thinking This Is Releated To A Buggy Update - Give Me Some Time And We Can Work This Out!!

Thank You For Your Waiting...:)

---

### Post by souneedalink on 2008-03-14
none of those will work, they will all report the same thing, the same error that he has been getting

if a package is unconfigured then until you deal with it that is all you will get

---

### Post by {BzF}~JOKesTER on 2008-03-14
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/)

It Seems I've Found That All 64Bit Ubuntu Gutsy Users Have The Same Error And I'm Pretty Sure {Accordding To The Above Bugs Report} That The Convict Is:

initramfs-tools

However I Can't Be To Sure...

You Can Try This Though:

READ BELOW FIRST!!!

sudo apt-get remove initramfs-tools

You Might Have To Type:

sudo apt-get remove initramfs-tools --force

I've Been Looking Around And It Seems This Problem Stil Hasn't Been Solved For Anyone Yet - But This Is Somthing That At Least Might Work - I Will Warn You However.

BACK UP YOUR PERSONAL DATA FIRST!!!!!

I Do Not Think This Should Cuase Your System To Crash - But It IS Possible And So {According To The Forums Rules} I Must Warn You!!!!

---

### Post by {BzF}~JOKesTER on 2008-03-14
Now Download And Install This:

[http://packages.debian.org/etch/all/initramfs-tools/download](http://packages.debian.org/etch/all/initramfs-tools/download)

---

### Post by utUtu on 2008-03-14
> **eebamxela said:**
> I know this has been talked about many times over but no matter how many times i follow the many instructions i get no where. Ubuntu started giving me this error after i ran an update. I can't download anything through synaptic or the add/remove apps menu. I'm running Ubuntu 7.10- the Gutsy Gibbon.

I input "sudo dpkg --configure -a" (yes with the "sudo") into the terminal and i get this:



Can anyone make any sense out of this?

Thanks.
Before you do anything else to make matters worse, what this means is that somehow it could not find the program /usr/bin/getopt.  Pls check if you have it.  If not on the terminal, execute locate getopt and post the results here.

Also pls post echo $PATH.  Then I can help you fix it.

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **utUtu said:**
> Before you do anything else to make matters worse, what this means is that somehow it could not find the program /usr/bin/getopt.  Pls check if you have it.  If not on the terminal, execute locate getopt and post the results here.

Also pls post echo $PATH.  Then I can help you fix it.

Possible This Might Be The File You Need:

Attached..:)

---

### Post by {BzF}~JOKesTER on 2008-03-14
utUtu,

Do You Think That Maybe It Is:

getopt?

I Was Thinking Maybe It Was The Updated inframs-tools
As Everyone Who's Updated Their 64BIT Gutsy Seems To Have This Problem.

I Don't Know Why The Update Whould Of Moved/Removed/Renamed The getopt Package.?

Just Wanted To See What You Thought About It.

Cheers!!!:)

---

### Post by utUtu on 2008-03-14
> **{BzF}~JOKesTER said:**
> utUtu,

Do You Think That Maybe It Is:

getopt?

I Was Thinking Maybe It Was The Updated inframs-tools
As Everyone Who's Updated Their 64BIT Gutsy Seems To Have This Problem.

I Don't Know Why The Update Whould Of Moved/Removed/Renamed The getopt Package.?

Just Wanted To See What You Thought About It.

Cheers!!!:)

Sorry but until the OP responds to my post, we are in the dark.

---

### Post by utUtu on 2008-03-14
> **{BzF}~JOKesTER said:**
> utUtu,

Do You Think That Maybe It Is:

getopt?

I Was Thinking Maybe It Was The Updated inframs-tools
As Everyone Who's Updated Their 64BIT Gutsy Seems To Have This Problem.

I Don't Know Why The Update Whould Of Moved/Removed/Renamed The getopt Package.?

Just Wanted To See What You Thought About It.

Cheers!!!:)

Like I said  it's the getopt not found.

```
 13: getopt: not found
```

---

### Post by {BzF}~JOKesTER on 2008-03-14
So Which Package Replaces get-opt??

The One I Gave Is The Primary.

---

### Post by souneedalink on 2008-03-14
> **souneedalink said:**
> 

Likely going to have to purge some critical stuff and take a chance on reinstalling it.

Step ONE - backup everything now!
Sounds reasonable doesn't it. :D I think the package that may be fubar'd is util-linux, I would start by seeing if I could use dpkg to remove it and reinstall it then try running the dpkg command again. 

Even with my small bean count I know how to lookup what package contains what and so forth...

---

### Post by {BzF}~JOKesTER on 2008-03-14
It Seems That dpkg is missing get-opt so i don't think that will work.

it gives him the error message everytime he types the 

apt-get 

line followed by anything else -{even when prefixed w/sudo}

thats why i'm trying to figure out what package he needs for get-opt

and i'll direct-link him to it - seeing as he can't access the reps.

---

### Post by souneedalink on 2008-03-14
> it gives him the error message everytime he types the 

apt-get 

line followed by anything else -{even when prefixed w/sudo}
Uh, I think I said that...


> **{BzF}~JOKesTER said:**
> It Seems That dpkg is missing get-opt so i don't think that will work.

dpkg isnt missing getopt, his system is...

> **{BzF}~JOKesTER said:**
> 
thats why i'm trying to figure out what package he needs for get-opt

and i'll direct-link him to it - seeing as he can't access the reps.

I didnt say to use apt I said dpkg and if dpkg isn't going to work then what is the point in direct linking him to a deb package. 

Shouldnt you first check and see if he has the getopt command available? See if util-linux package is installed? Possibly reinstall it? Or possibly check and make sure his path variable is set correctly?

size doesn't matter.....proof is in the pudding... :lolflag:

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **souneedalink said:**
> Uh, I think I said that...



dpkg isnt missing getopt, his system is...



I didnt say to use apt I said dpkg and if dpkg isn't going to work then what is the point in direct linking him to a deb package. 

Shouldnt you first check and see if he has the getopt command available? See if util-linux package is installed? Possibly reinstall it? Or possibly check and make sure his path variable is set correctly?

size doesn't matter.....proof is in the pudding... :lolflag:

The Point Is Is That dpkg Needs get-opt

Ok>>??

Cheers!:)

---

### Post by souneedalink on 2008-03-14
no, mkinitramfs needs getopt

---

### Post by {BzF}~JOKesTER on 2008-03-14
> **souneedalink said:**
> no, mkinitramfs needs getopt

Your Right - Sorry My Bad....:(

---

### Post by eebamxela on 2008-03-15
every time i initiate the installation of ANY file, the installer tells me this:

> Only one software management tool is allowed to run at the same time.

I checked the system monitor for any programs that might be the culprit for this error, but nothing else is open.

Forgive my noobyness, is there a way to install something through the terminal?


the results from those other lines of code are here:

> eebamxela@LapityTop:~$ locate getopt
/usr/lib/python2.5/getopt.pyc
/usr/lib/python2.5/getopt.py
/usr/lib/python2.5/distutils/fancy_getopt.py
/usr/lib/python2.5/distutils/fancy_getopt.pyc
/usr/share/guile/1.6/ice-9/getopt-long.scm
/usr/share/perl/5.8.8/newgetopt.pl
/usr/share/perl/5.8.8/getopts.pl
/usr/share/perl/5.8.8/getopt.pl
eebamxela@LapityTop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by {BzF}~JOKesTER on 2008-03-15
Ok IDK If This Will Work But Try Placing These Files In The :

/usr/sbin/mkinitramfs

Folder:)

---

### Post by dylanologist on 2008-03-18
I'm having the exact same problem as described on 7.10 64-bit Ubuntu.  Was going to attempt the possible fix suggested above, but usr/sbin/mkinitramfs is not a directory, so how would I add those files?

---

### Post by dylanologist on 2008-03-18
I'm also wondering if anyone has any thoughts about whether upgrading to the 8.04 Beta release due out any day now would likely address this problem.  I assume I would have to do a fresh install from CD, but I have my data backed up and if it would mean that I could use Add/Remove, Synaptic, and Update Manager again it would be worth the trouble.

However, I'm worried that after going to the trouble of reinstalling the same bug could be present in the new version.  Anyone wish to venture a guess as to how likely that is?

---

### Post by Pumalite on 2008-03-18
I have Hardy heron running in a Core 2 Duo. This is my file:
#!/bin/sh

umask 0022

# Defaults
keep="n"
CONFDIR="/etc/initramfs-tools"
verbose="n"
errors_to="2>/dev/null"
BUSYBOXDIR="/usr/lib/initramfs-tools/bin/"
# BUSYBOXDIR="/bin"

OPTIONS=`getopt -o d:ko:r:v --long supported-host-version:,supported-target-version: -n "$0" -- "$@"`

# Check for non-GNU getopt
if [ $? != 0 ] ; then echo "Terminating..." >&2 ; exit 1 ; fi

eval set -- "$OPTIONS"

while true; do
	case "$1" in
	-d)
		CONFDIR="$2"
		shift 2
		if [ ! -d "${CONFDIR}" ]; then
			echo "${0}: ${CONFDIR}: Not a directory" >&2
			exit 1
		fi
		;;
	-o)
		outfile="$2"
		shift 2
		;;
	-k)
		keep="y"
		shift
		;;
	-r)
		ROOT="$2"
		shift 2
		;;
	-v)
		verbose="y"
		shift
		;;
	--supported-host-version)
		supported_host_version="$2"
		shift 2
		;;
	--supported-target-version)
		supported_target_version="$2"
		shift 2
		;;
	--)
		shift
		break
		;;
	*)
		echo "Internal error!" >&2
		exit 1
		;;
	esac
done

if [ -n "$supported_host_version" ] || [ -n "$supported_target_version" ]; then
	if [ -n "$supported_host_version" ]; then
		host_upstream_version="${supported_host_version%%-*}"
	fi
	if [ -n "$supported_target_version" ]; then
		target_upstream_version="${supported_target_version%%-*}"
		if dpkg --compare-versions "$target_upstream_version" lt "2.6.12"; then
			exit 2
		fi
	fi
	echo "Depreciation warning: use ramdisk=mkinitramfs-kpkg."
	exit 0
fi

# For dependency ordered mkinitramfs hook scripts.
. /usr/share/initramfs-tools/scripts/functions
. /usr/share/initramfs-tools/hook-functions

. "${CONFDIR}/initramfs.conf"
EXTRA_CONF=''
for i in /usr/share/initramfs-tools/conf.d/* ${CONFDIR}/conf.d/*; do
	EXTRA_CONF="${EXTRA_CONF} $(basename $i | grep '^[a-z0-9][a-z0-9\._-]*$' | grep -v '\.dpkg-.*$')";
done
for i in ${EXTRA_CONF}; do
	if [ -e  ${CONFDIR}/conf.d/${i} ]; then
		. ${CONFDIR}/conf.d/${i}
	elif [ -e  /usr/share/initramfs-tools/conf.d/${i} ]; then
		. /usr/share/initramfs-tools/conf.d/${i}
	fi
done

if [ -n "${UMASK}" ]; then
	umask "${UMASK}"
fi

if [ -z "${outfile}" ]; then
	usage
fi

touch "$outfile"
outfile="$(readlink -f "$outfile")"

# And by "version" we really mean path to kernel modules
# This is braindead, and exists to preserve the interface with mkinitrd
if [ ${#} -ne 1 ]; then
	version="$(uname -r)"
else
	version="${1}"
fi

# Check that we're using a new enough kernel version, first for ourselves,
# then for each of the hooks, which can have a MINKVER variable defined
check_minkver ${version}
check_minkver ${version} /usr/share/initramfs-tools/hooks
check_minkver ${version} ${CONFDIR}/hooks

case "${version}" in
/lib/modules/*/[!/]*)
	;;
/lib/modules/[!/]*)
	version="${version#/lib/modules/}"
	version="${version%%/*}"
	;;
esac

case "${version}" in
*/*)
	echo "$PROG: ${version} is not a valid kernel version" >&2
	exit 1
	;;
esac

if [ -d "${outfile}" ]; then
	echo "${outfile} is a directory"
	exit 1
fi

MODULESDIR="/lib/modules/${version}"

if [ ! -e "${MODULESDIR}" ]; then
	echo "Cannot find ${MODULESDIR}"
	exit 1
fi
if [ ! -e "${MODULESDIR}/modules.dep" ]; then
	depmod ${version}
fi

DESTDIR="$(mktemp -t -d mkinitramfs_XXXXXX)" || exit 1
__TMPCPIOGZ="$(mktemp -t mkinitramfs-OL_XXXXXX)" || exit 1

DPKG_ARCH=`dpkg --print-installation-architecture`

# Export environment for hook scripts.
#
export MODULESDIR
export version
export CONFDIR
export DESTDIR
export DPKG_ARCH
export verbose

# Private, used by 'catenate_cpiogz'.
export __TMPCPIOGZ

for d in bin conf/conf.d etc lib modules sbin scripts ${MODULESDIR}; do
	mkdir -p "${DESTDIR}/${d}"
done

# MODULES=list case.  Always honour.
for x in "${CONFDIR}/modules" /usr/share/initramfs-tools/modules.d/*; do
	if [ -f "${x}" ]; then
		add_modules_from_file "${x}"
	fi
done

if [ "${MODULES}" = "dep" ]; then
	dep_add_modules
fi

if [ "${MODULES}" = "most" ]; then
	auto_add_modules
fi

if [ "${MODULES}" = "netboot" ]; then
	auto_add_modules base
	auto_add_modules net
fi

# Have to do each file, because cpio --dereference doesn't recurse down
# symlinks.

# klibc
ln -s /usr/lib/klibc/bin/* ${DESTDIR}/bin
ln -s /lib/klibc-*.so ${DESTDIR}/lib
copy_exec /usr/share/initramfs-tools/init /init
cp -a /usr/share/initramfs-tools/scripts/* "${DESTDIR}/scripts"
for f in $(cd ${CONFDIR}/scripts && \
	find . \( -name '*.dpkg*' -prune -o -name '*~' -prune \) \
		-o -type f -print); do
	mkdir --parents "${DESTDIR}/scripts/$(dirname "${f}")"
cp -p "${CONFDIR}/scripts/${f}" "${DESTDIR}/scripts/$(dirname "${f}")"
done
echo "DPKG_ARCH=${DPKG_ARCH}" > ${DESTDIR}/conf/arch.conf
copy_exec "${CONFDIR}/initramfs.conf" /conf
for i in ${EXTRA_CONF}; do
	if [ -e "${CONFDIR}/conf.d/${i}" ]; then
		copy_exec "${CONFDIR}/conf.d/${i}" /conf/conf.d
	elif [ -e "/usr/share/initramfs-tools/conf.d/${i}" ]; then
		copy_exec "/usr/share/initramfs-tools/conf.d/${i}" /conf/conf.d
	fi
done

# ROOT hardcoding
if [ -n "${ROOT}" ]; then
	echo "ROOT=${ROOT}" > ${DESTDIR}/conf/conf.d/root
fi

# Busybox
if [ "x${BUSYBOX}" = "xn" ]; then
	ln -s ${DESTDIR}/bin/sh.shared ${DESTDIR}/bin/sh
	echo "Warning: Busybox is required for successful boot!"
else
	rm -f ${DESTDIR}/bin/sh
	rm -f ${DESTDIR}/bin/busybox
	copy_exec ${BUSYBOXDIR}/busybox /bin/busybox
	ln -s ${BUSYBOXDIR}/busybox ${DESTDIR}/bin/sh
fi

# Modutils
copy_exec /sbin/modprobe /sbin
copy_exec /sbin/depmod /sbin
copy_exec /sbin/rmmod /sbin
mkdir -p "${DESTDIR}/etc/modprobe.d"
cp -a /etc/modprobe.d/* "${DESTDIR}/etc/modprobe.d"

run_scripts /usr/share/initramfs-tools/hooks
run_scripts "${CONFDIR}"/hooks

# FIXME: Remove this Raid block after Etch releases
if [ -x /sbin/mdadm ] && [ ! -f /usr/share/initramfs-tools/hooks/mdadm ]; then
	# use mkinitrd magic for Sarge backwards compat
	rootraiddev="$(df / | sed -rne 's,^(/dev/[^[:space:]]+).*,\1,p')"
	echo "rootraiddev=${rootraiddev}" > ${DESTDIR}/conf/mdrun.conf
	mdadm=$(mdadm --detail "${rootraiddev}")
	echo "${mdadm}" | awk '
		$1 == "Number" && $2 == "Major" { start = 1; next }
		$1 == "UUID" { print "uuid=" $3; next }
		!start { next }
		$2 == 0 && $3 == 0 { next }
		{ devices = devices " " $NF }
		END { print "devices='\''" devices "'\''" }' \
		>> ${DESTDIR}/conf/mdrun.conf
	copy_exec /sbin/mdadm /sbin
	for x in md linear multipath raid0 raid1 raid456 raid5 raid6 raid10; do
		manual_add_modules ${x}
	done
fi
[ -x /sbin/mdrun ] && copy_exec /sbin/mdrun /sbin

# FIXME: Remove this LVM block after Etch releases
if [ -x /sbin/vgchange ] && [ -d /lib/lvm-200 ] \
	&& [ ! -f /usr/share/initramfs-tools/hooks/lvm2 ]; then
	copy_exec /lib/lvm-200/vgchange /sbin
	for x in dm_mod dm_snapshot dm_mirror; do
		manual_add_modules ${x}
	done
fi

# Apply DSDT to initramfs
if [ -e "${CONFDIR}/DSDT.aml" ]; then
	copy_exec "${CONFDIR}/DSDT.aml" /
fi

[ "${verbose}" = y ] && echo "Building cpio ${outfile} initramfs"
(cd "${DESTDIR}" && find . | cpio --quiet --dereference -o -H newc | gzip >"${outfile}") || exit 1

if [ -s "${__TMPCPIOGZ}" ]; then
	cat "${__TMPCPIOGZ}" >>"${outfile}" || exit 1
fi

if [ "${keep}" = "y" ]; then
	echo "Working files in ${DESTDIR} and overlay in ${__TMPCPIOGZ}"
else
	rm -rf "${DESTDIR}"
	rm -rf "${__TMPCPIOGZ}"
fi

exit 0

I've had no problems and I love the OS.

---

### Post by utUtu on 2008-03-18
> **eebamxela said:**
> every time i initiate the installation of ANY file, the installer tells me this:



I checked the system monitor for any programs that might be the culprit for this error, but nothing else is open.

Forgive my noobyness, is there a way to install something through the terminal?


the results from those other lines of code are here:

Somehow you lots getopt.  Not sure why.  But anyway, copy the attached file to /usr/bin as root.

Then, do dpkg  --configure -a

I hope it will fix the problem, assuming there is nothing else you lost.

Good luck!!!

---

### Post by dylanologist on 2008-03-18
Thanks ututu, but I don't see an attached file.  Am I missing something, or perhaps you've just forgotten to attach it.

---

### Post by utUtu on 2008-03-19
> **dylanologist said:**
> Thanks ututu, but I don't see an attached file.  Am I missing something, or perhaps you've just forgotten to attach it.

Sorry I didn't realize it did not go through.  Hope it does this time

---

### Post by dylanologist on 2008-03-19
Thanks utUtu,

That file seems to have fixed the major problems I was having.  I still get the "Partial Upgrade" message when I start Update Manager (I don't know if this is in any way related to the other problems I was having), but I am now able to download and install updates, as well as use Add/Remove and Synaptic.

Hope this works for others as well.  Cheers!

---

### Post by utUtu on 2008-03-19
> **dylanologist said:**
> Thanks utUtu,

That file seems to have fixed the major problems I was having.  I still get the "Partial Upgrade" message when I start Update Manager (I don't know if this is in any way related to the other problems I was having), but I am now able to download and install updates, as well as use Add/Remove and Synaptic.

Hope this works for others as well.  Cheers!

My pleasure to be of help.  Glad to hear you are back to normal..sort of..:)
Anyway, I haven't used gNome for a while, but in Synaptics there used to be a button 'Show details'.  See if it tells you something.  Also, there is an option to 'fix broken dependencies' somewhere.  Usually, these are some packages that have 'un-met dependencies' which ususally are versions issues.  Otherwise, you are good but not the latest versions.

I normally use aptitude on the konsole.  On the terminal as root execute these in order

sudo aptitude update   <--- updates the packages
sudo aptitude safe-upgrade  <-- tries to upgrade

You will see lots of useful info like packages tio be upgraded, kept back,..,etc

If you see something, you need from the 'kept back' list, you can force it to install and it will install added dependencies by

sudo aptitude install *must-have-pack*

Of course it will always ask for your confirmation.  If you are not sure then answer 'n'.

---

### Post by paulnewby on 2008-03-19
Hello all, 

sorry to come in here.....but iam having the same problem ;-(

I have tried everything now with no success

can some one please help??

---

### Post by paulnewby on 2008-03-19
This is the error i am getting

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 8, in <module>
    import sys,os,os.path,shutil,tempfile
ImportError: No module named shutil
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up libkrb53 (1.6.dfsg.1-7ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by eebamxela on 2008-03-20
I still can't get any of this **** to work. If Ubuntu doesn't come out with a fix within the next few days, I'm reinstalling it.

---

### Post by kiroro on 2008-03-21
I am having EXACTLY the same problem as OP. The system is 7.10 too. So frustrated.

I copied 'getopt' to /usr/bin and ran 'sudo dpkg --configure -a' again, got this:

```

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


dpkg: dependency problems prevent configuration of realplay:
 realplay depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing realplay (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 realplay 
```

Looks like something is still wrong...but at least I can run 'sudo aptitude update' and 'sudo aptitude safe-upgrade' now.

---

### Post by kiroro on 2008-03-22
Now my output of sudo dpkg --configure -a is:

```

dpkg: dependency problems prevent configuration of realplay:
 realplay depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing realplay (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplay 
```

Am I missing packages like libstdc++5? 

Or Is it something to do with realplayer? I force-installed i386-realplayer 10 in my AMD64 system before. It works pretty well, but I heard I had to get it from the multiverse repository?

UPDATE1:
OK, I checked the Synaptic Package Manager and found my system already has libstdc++6- 4.1- dev. There is also libstdc++5- 3.3- dev available. Should I install it? I don't know what they mean...

UPDATE2:
Problem is solved by 'sudo apt-get install libstdc++5'. Now sudo dpkg --configure -a returns:
```
Setting up realplay (10.0.9-0feisty1) ...
```
So I learned that one had to install libstdc++5 first in order to play with realplayer10...

Reference: [http://real.lithium.com/real/board/print?board.id=realplayer&message.id=1152&page=1&format=page](http://real.lithium.com/real/board/print?board.id=realplayer&message.id=1152&page=1&format=page)

---

### Post by kiroro on 2008-03-22
> **eebamxela said:**
> I still can't get any of this **** to work. If Ubuntu doesn't come out with a fix within the next few days, I'm reinstalling it.

Copying 'getopt' to /usr/bin does not work for you? That's really odd...
This solved most of the my problems like 'could not use apt-get, could not update or install' etc.

---

### Post by ABorges on 2008-03-23
Hi

I have same problem here.

any apt-get results on :
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

or something like below 
```

 sudo apt-get -clean
E: Abrindo arquivo de configuração lean - ifstream::ifstream (2 files or folders missing)

```


and dpkg results below output
```

 sudo dpkg --configure -a
Instalando initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Instalando linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: erro processando linux-image-2.6.22-14-generic (--configure):
 subprocesso post-installation script retornou código de saída de error 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocesso post-installation script retornou código de saída de error 1


```

my uname -a is :

Linux cafebrasil-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

---

### Post by Zeral on 2008-04-02
Same problem here, doens't matter if i do:
apt-get -f  install
apt-get upgrade
dpkg --configure -a
or
apt-get autoremove

all end in exactly the same result:
> Failed to run depmod
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help, don't know what to do and not being able to install any app or do any update...

---

### Post by Zeral on 2008-04-09
bump

---

### Post by joe_herz on 2008-04-09
I'm having the same problems. Can't run Updates, can't install anything. I've copied getopt to USR\BIN folder and still can't run any upgrades or install anything.

Error msg after running sudo aptitude update:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

If I run dpkg --configure -a 
The message I get is:
> dpkg: requested operation requires superuser privilege

Even though I'm logged in as root...

---

### Post by Zeral on 2008-04-11
And when not being logged on as root but performing 'sudo dpkg --configure -a' instead?

---

### Post by SimonRoberthson on 2008-04-18
Okey this i probably a dumb question but how/what do I do with the attached getopt.tar.gz file?
I mean I know how to unpack it and all that but should I put the whole folder in /usr/bin or just so file (in that case which file). Putting the whole folder in /usr/bin gave me...

```
simon@Gobblin:$ sudo dpkg --configure -a
Ställer in initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Ställer in linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: Permission denied
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: fel vid hantering av linux-image-2.6.22-14-generic (--configure):
 underprocess post-installation script gav felkod 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: Permission denied
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: underprocess post-installation script gav felkod 1

```

Sry for the language but I'm from Sweden (the coolest country of them all) :P 
Please help i don't wanna reinstall because it took me ages to fix my graphics's.

---

### Post by jicarre on 2008-04-22
Hi, 



I am having the same trouble than you. Did you find what to do ?

You will be kind to let we know. I am really pist off because I am stocked without being able to dowload, install or update my PC.

Thanks in advance

---

### Post by Alyxandor on 2008-05-01
> **jicarre said:**
> Hi, 



I am having the same trouble than you. Did you find what to do ?

You will be kind to let we know. I am really pist off because I am stocked without being able to dowload, install or update my PC.

Thanks in advance

...No worries friend!  It's page five you're looking for:

[http://ubuntuforums.org/showthread.php?t=724273&page=5](http://ubuntuforums.org/showthread.php?t=724273&page=5)

The getopt file is at:

[http://ubuntuforums.org/attachment.php?attachmentid=63070&d=1205901665](http://ubuntuforums.org/attachment.php?attachmentid=63070&d=1205901665)

And, if you're system got as fuxored by an incomplete hardy upgrade like mine, you may not be able to open a file-browser window.  If this bites yer behind, I recommend opening the tarball in mozilla? download window, navigate to the file, extract somewhere that you have regular privileges like /home, then sudo cp /home/getopt /usr/bin {I just auto-su to make life easier)...  

Then, try getopt at term to make sure it's running, and retry the dpkg --configure -a

PEACE!

---

### Post by Alyxandor on 2008-05-01
PS - Almost undoubtably, you are running an 'amd64' version of Ubuntu, and possibly broke the getopt during a failed update.  Seems to be a common problem, mainly involving the general lack of 64-bit compiled binary-anything...  Over the last day or so I've been doing as many automatic updates and junk as my time allows, and it seems to be getting better.  My advice is to download a fresh copy of Hardy for 386, and dual boot to different roots...  Cos I really like the 64-bit speed on the imaging apps and junk, but 32-bit reliability is a feature of its own!

PPS - What a long PS, eh?

---

### Post by rstritmatter on 2008-06-08
> **{BzF}~JOKesTER said:**
> Try And Go Ointo Synaptic And Under "Repositories" On The Toolbar Check All The Boxes In All The Tabs.....

I was having the same error message -- I did this first, and it worked. Thanks.

---

### Post by grrregistration on 2008-06-09
Okay, so I copied the getopt file but it returns this error when I try to run it:

bash: /usr/bin/getopt: cannot execute binary file


Can you help me get this running?

EDIT:

I ran it as root but now I have this error:
/usr/bin/getopt: 1: Syntax error: ")" unexpected

---

### Post by netspyman on 2008-07-08
im getting this error now after i copied the getopt file into usr/bin

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
/usr/sbin/mkinitramfs: line 13: /usr/bin/getopt: cannot execute binary file
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

I have tried everything any help would be great thanks

NETSPYMAN

---

