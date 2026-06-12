---
title: "Synaptic won't remove an application"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by mawcs on 2009-12-02
I was checking out some various packages and tried out micro-httpd (bad mistake).  It wouldn't install properly.  OK, I'm experimenting, I expected this possibility.  Here's the problem, when I "mark for removal" and "apply" I receive the following error:

```
E: micro-httpd: subprocess installed pre-removal script returned error exit status 100
```I'm new to the aptitude process and I'm not entirely sure what to do to completely remove it and FORCE it to work.  I'm inclined to just leave it except that Apache won't install now that this thing is here.

Any help would be greatly appreciated.

---

### Post by mawcs on 2009-12-02
I'm adding this additional information, in case it is useful for solving this problem.  When I run apt-get remove, I receive the following:

```

$ sudo apt-get -f remove micro-httpd                      
Reading package lists... Done                                                                
Building dependency tree                                                                     
Reading state information... Done                                                            
The following packages were automatically installed and are no longer required:              
  kimagemapeditor kxsldbg libgcj-common                                                      
Use 'apt-get autoremove' to remove them.                                                     
The following packages will be REMOVED:                                                      
  micro-httpd                                                                                
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.                               
After this operation, 81.9kB disk space will be freed.                                       
Do you want to continue [Y/n]? y                                                             
(Reading database ... 205445 files and directories currently installed.)                     
Removing micro-httpd ...                                                                     
/var/lib/dpkg/info/micro-httpd.prerm: removing /etc/inetd.conf entry                         
invoke-rc.d: unknown initscript, /etc/init.d/inetd not found.                                
dpkg: error processing micro-httpd (--remove):                                               
 subprocess installed pre-removal script returned error exit status 100                      
Errors were encountered while processing:                                                    
 micro-httpd                                                                                 
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Soul-Sing on 2009-12-02
```
sudo dpkg --remove --force-remove-reinstreq micro-httpd
```

---

### Post by mawcs on 2009-12-02
```
$ sudo dpkg --remove --force-remove-reinstreq micro-httpd
(Reading database ... 207372 files and directories currently installed.)
Removing micro-httpd ...
/var/lib/dpkg/info/micro-httpd.prerm: removing /etc/inetd.conf entry
invoke-rc.d: unknown initscript, /etc/init.d/inetd not found.
dpkg: error processing micro-httpd (--remove):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 micro-httpd
```

---

### Post by Soul-Sing on 2009-12-02
is there in the background a process busy with that name?
then you could kill that process, and try to remove it again.

---

### Post by Soul-Sing on 2009-12-02
```
gksudo nautilus
```

/var/lib/dpkg/info
/var/lib/dpkg/status
try to remove the package with a keyword in the "search-option".

---

### Post by Soul-Sing on 2009-12-02
> **leoquant said:**
> ```
gksudo nautilus
```

/var/lib/dpkg/info
/var/lib/dpkg/status
try to remove the package with a keyword in the "search-option".
or search for broken packages.

---

### Post by mawcs on 2009-12-02
When I look at the installed files, I see:

/.
/usr
/usr/sbin
/usr/sbin/micro-httpd
/usr/share
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/micro-httpd.8.gz
/usr/share/doc
/usr/share/doc/micro-httpd
/usr/share/doc/micro-httpd/NEWS.Debian.gz
/usr/share/doc/micro-httpd/README.Debian-source
/usr/share/doc/micro-httpd/copyright
/usr/share/doc/micro-httpd/changelog.Debian.gz

I am assuming that /usr/sbin/micro-httpd is the executable.  I really don't see any other possibility. There's nothing running with that image name:

```
$ ps -ef | grep micro-httpd
m***  16472  2326  0 11:04 pts/1    00:00:00 grep --color=auto micro-httpd
$ ps -ef | grep micro
m***  16494  2326  0 11:05 pts/1    00:00:00 grep --color=auto micro
$ ps -ef | grep httpd
m***  16499  2326  0 11:05 pts/1    00:00:00 grep --color=auto httpd
```

(I've obscured my local username for my security)

---

### Post by mawcs on 2009-12-02
> **leoquant said:**
> or search for broken packages.

I'm not sure how to do that.  Am I just looking at text files to find references to these packages?  How do I go about actually removing everything?

---

### Post by Soul-Sing on 2009-12-02
> **mawcs said:**
> I'm not sure how to do that.  Am I just looking at text files to find references to these packages?  How do I go about actually removing everything?

on the rightop of your screen there is a search-option possibility.
(at least in hardy heron...)
/var/lib/dpkg/info
/var/lib/dpkg/status
are no refer. to the package at all?

---

### Post by mawcs on 2009-12-02
OK, did the "searching" you suggested.  In /var/lib/dpkg/info, I find the following files:

micro-httpd.list
micro-httpd.md5sums
micro-httpd.postinst
micro-httpd.prerm

In  /var/lib/dpkg/status, I find the following:

Package: micro-httpd
Status: deinstall ok installed
Priority: optional
Section: web
Installed-Size: 80
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: amd64
Version: 20051212-10
Provides: httpd
Depends: libc6 (>= 2.4), openbsd-inetd | inet-superserver | micro-inetd | netcat-traditional
Suggests: micro-proxy
Description: really small HTTP server
 A very small HTTP server implemented in 150 lines of code.
 Program can be used to serve HTTPS by wrapping it with stunnel.
 It implements all the basic features of an HTTP server, including:
 .
   * Security against ".." filename snooping
   * The common MIME types
   * Trailing-slash redirection
   * index.html
   * Directory listings
Original-Maintainer: Jari Aalto <jari.aalto@cante.net>
Homepage: [http://www.acme.com/software/micro_httpd](http://www.acme.com/software/micro_httpd)

I'm not sure what to do with this information.  Is there some possibility of fixing the scripts?

---

### Post by Soul-Sing on 2009-12-02
> Is there some possibility of fixing the scripts?

thats THE question. I am not sure...

---

### Post by mawcs on 2009-12-02
> **leoquant said:**
> thats THE question. I am not sure...

Well, the .prerm script is fairly short.  It is attempting to remove itself from the /etc/inetd.conf.  Looking at the file, there is  nothing pertaining to micro-httpd in the conf file.  The entirety of the conf file is a single line which doesn't seem to pertain to micro-httpd:

```
#<off># netbios-ssn    stream    tcp    nowait    root    /usr/sbin/tcpd    /usr/sbin/smbd
```

Here is the .prerm:

```

#!/bin/sh

set -e

PATH="/sbin:/bin:/usr/sbin:/usr/bin"
PACKAGE=$(basename $0 | sed 's/\..*//')
pkgdir=/usr/share/$PACKAGE
conf=/etc/inetd.conf
port="www"
entry=

Die ()
{
    echo "$0: $*" >&2
    exit 1
}

IsInetd ()
{
    [ -x /usr/sbin/update-inetd ]
}

Debhelper ()
{
    :
    
}

InetdName ()
{
    name=inetd

    if [ -f /etc/init.d/openbsd-inetd ]; then
        name="openbsd-inetd"
    elif [ -f /etc/init.d/rlinetd ]; then
        name="rlinetd"
    fi

    echo $name
}

MainInetd ()
{
    if [ "$1" = "remove" ]; then

    echo "$0: removing $conf entry" >&2
    update-inetd --group STANDARD --remove "$port.*$PACKAGE"
    invoke-rc.d $(InetdName) reload
    fi
}

Main ()
{
    IsInetd && MainInetd "$@"
    Debhelper
}

Main "$@"

# End of file

```

I'm going to take a risk and change the Die() function to return 0 instead of 1.  I'll see if that fixes it.

---

### Post by mawcs on 2009-12-02
No dice. :(

---

### Post by mawcs on 2009-12-02
HA! :-D

Commented out the checks in Main():

```
Main ()
{
#    IsInetd && MainInetd "$@"
    Debhelper
}
```

Removing micro-httpd worked!  Thanks so much for your help.

---

### Post by Soul-Sing on 2009-12-02
Nice job mawcs! Glad you'r out of troubles.:p

---

