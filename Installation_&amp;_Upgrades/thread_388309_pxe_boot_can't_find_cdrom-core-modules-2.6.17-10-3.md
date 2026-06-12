---
title: "pxe boot: can't find cdrom-core-modules-2.6.17-10-386-di_2.6.17.1-10.34_i386.udeb"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by blobbb on 2007-03-19
hello,
We had a running install server via pxeboot and kickstart files for 2 weeks.
We have uploaded the iso and use an apache to serve the install files to the clients.
We could do ubuntu (and other disto's) install in 10minutes unattended.

Now the ubuntu install is 'broken'.  The client tries to download a newer version of the cdrom-core-modules, this is the apache access log:
```
[Fri Mar 16 14:07:30 2007] [error] [client 192.168.178.66] File does not exist: /Storage/data/mounts/x86/ubuntu-6.10/pool/main/l/linux-source-2.6.17/
cdrom-core-modules-2.6.17-10-386-di_2.6.17.1-**10.34**_i386.udeb
```
the version on the cd is:
cdrom-core-modules-2.6.17-10-386-di_2.6.17-**10.33**_i386.udeb
Then the installer asks to choose a mirror.
I saw there is a security problem in that version so i assume somewhere in the install it checks for updates and goes for the newer version.  
Did somebody else had this problem?  Are there solutions for it?
The nice solution would be to be able to update the iso on the install server.
But i don't find any information on that.
Thx for any help/tips!

---

### Post by blobbb on 2007-03-20
ok i found the solution, replace the iso's with a local mirror and a cron job to keep the mirror up to date.

#apt-get install debmirror

#cat /etc/debmirror.conf

```

# Output options
$verbose=1;
$progress=1;
$debug=0;

# Download options
$host="ftp.belnet.be/linux/ubuntu/";
#$host="archive.ubuntu.com";
#$user="anonymous";
#$passwd="anonymous@";
$remoteroot="ubuntu/";
$download_method="http";
@dists="**edgy,edgy-security,edgy-updates**";
@sections="**main,main/debian-installer,restricted,restricted/debian-installer**";
@arches="i386";
# @extra_dirs="";
# @ignores="";
# @excludes="";
# @includes="";
# @excludes_deb_section="";
# @limit_priority="";
$skippackages=0;
$getcontents=0;
$do_source=0;
$max_batch=0;



# Security/Sanity options
$ignore_release_gpg=1;
$ignore_release=0;
$check_md5sums=0;
$ignore_small_errors=0;

# Cleanup
$cleanup=0;
$post_cleanup=1;

# Locking options
$timeout=300;

# Rsync options
$rsync_batch=200;
$rsync_options="-aIL --partial";

# FTP/HTTP options
$passive=0;
# $proxy="http://proxy:port/";

# Dry run
$dry_run=0;

# Don't keep pdiff files but use them
$pdiff_mode="use";

# The config file must return true or perl complains.
# Always copy this.
1;
```

# debmirror /your/local/mirror/location

bye!

---

