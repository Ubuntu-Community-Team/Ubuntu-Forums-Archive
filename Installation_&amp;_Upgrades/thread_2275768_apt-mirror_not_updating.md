---
title: "apt-mirror not updating"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by sombrafam on 2015-04-28
Hi,


I seem to have a problem getting apt-mirror to update from a network mirror to a local mirror, the contents of my /etc/apt-mirror are:

```

############# config ###################
set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse                                                                                                         
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse                                                                                                        
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse                                                                                                       


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse


# 32 bits
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse


# 64 bits
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse


# 32 bits puppet
deb-i386 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty main
deb-i386 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty dependencies
deb-i386 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty devel


# Puppetlabs products
deb [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty main
deb-src [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty main


# Puppetlabs dependencies
deb [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty dependencies
deb-src [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty dependencies


# Puppetlabs devel (uncomment to activate)
deb [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty devel
deb-src [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty devel


# 64 bits
deb-amd64 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty main
deb-amd64 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty dependencies
deb-amd64 [http://apt.puppetlabs.com](http://apt.puppetlabs.com) trusty devel


clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
clean [http://apt.puppetlabs.com](http://apt.puppetlabs.com)

```

When I run apt-mirror I get:

```

 root@fit-hds-ftp:/home/ubuntu# apt-mirror Downloading 491 index files using 20 threads...
Begin time: Tue Apr 28 10:00:22 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Tue Apr 28 10:00:45 2015


Processing tranlation indexes: [TTTTTTTTTTTTTTTTTTTTTTTT]


Downloading 738 translation files using 20 threads...
Begin time: Tue Apr 28 10:00:45 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Tue Apr 28 10:01:07 2015


Processing indexes: [SSSSSSSSPPPPPPPPPPPPPPPPPPPPPPPP]


0 bytes will be downloaded into archive.
Downloading 0 archive files using 0 threads...
Begin time: Tue Apr 28 10:01:33 2015
[0]... 
End time: Tue Apr 28 10:01:33 2015


0 bytes in 0 files and 0 directories can be freed.
Run /var/spool/apt-mirror/var/clean.sh for this purpose.


Running the Post Mirror script ...
(/var/spool/apt-mirror/var/postmirror.sh)


Removing 0 unnecessary files [0 bytes]...
done.


Removing 0 unnecessary directories...
done.




Post Mirror script has completed. See above output for any possible errors.

```

But, when I run apt-get update && apt-get upgrade in the host, which is configured to use this server as a mirror nothing is downloaded, and I know there are new files. 
Any idea about this error?

---

### Post by dino99 on 2015-04-28
a detailed howto [http://www.tecmint.com/setup-local-repositories-in-ubuntu/](http://www.tecmint.com/setup-local-repositories-in-ubuntu/)
an other one [http://linoxide.com/ubuntu-how-to/setup-local-repository-ubuntu/](http://linoxide.com/ubuntu-how-to/setup-local-repository-ubuntu/)

---

