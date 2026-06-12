---
title: "Subversion and HTTPS bug in Intrepid 8.10 - workaround"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dcrooke on 2008-10-15
If you have upgraded to 8.10 you may suddenly find that using svn against a private https repository no longer works. It refuses to talk to the repository, with the following error:

svn: OPTIONS of 'https://xxxxxxxxxx.xxxx.xx/svn/repo': SSL negotiation failed: SSL error: Key usage violation in certificate has been detected. ([https://xxxxxxxxxxx.xxxx.xx](https://xxxxxxxxxxx.xxxx.xx))

This is because in Intrepid, the neon HTTP library, which Subversion uses to talk to HTTP(S) servers, has been built with GNU TLS instead of OpenSSL.

The GNU TLS implementation is pedantic about the usage bit flags in the certificate, and will simply refuse to connect if they are not exactly as per the standards specification. This is not something FSF will be prepared to fix - there is a bug report out to which they responded with rhetoric quoting RFC's. I love open source, but I like the "just make it work" philosophy instead (hence why I use Ubuntu and not Fedora :-)

The workaround I used is as follows:

Pull the Subversion and Subversion Deps source trees from the tigris site, and untar them in the same place:

Go into the subversion-1.xx/neon directory ....

# neon will by default build with OpenSSL and not GNU TLS
# The main subversion build is supposed to build it, but it had
# problems on my amd64 setup, so I had build it separately
./configure --with-ssl --with-pic   
make
make install

cd ..
rm -rf neon
edit /etc/ld.so.conf and add /usr/local/lib
ldconfig

# now build subversion with the OpenSSL-enabled neon
./configure --with-ssl --with-neon=/usr/local
make
make install

# get rid of /usr/bin/svn
dpkg --purge subversion

---

### Post by 11hjpphty76lkjj on 2008-10-29
Thank you SO much for posting this.

However I'm not sure what files I need to download specifically from subversion. Can you please post a link to the files you downloaded?

Thanks!!

Aaron

---

### Post by 11hjpphty76lkjj on 2008-10-29
I got it working.  I created a script to help other people.  You can run the script by running the following command as USER:

```
sh subversion_certfix.sh
```The script:

```

#!/bin/sh
echo "This script will reconfigure subversion to work with certs correctly."
echo "Steps outlined by dcrooke and compiled into this script by Kalosaurusrex"
echo "Please see the ubuntuforums.org thread for more information, questions or help."
echo "http://ubuntuforums.org/showthread.php?p=6057983"
echo ""
echo ""
echo "Please run this script as USER ONLY."
echo ""
echo "Press control-c to quit..else the script will start in 5 seconds."
sleep 5
sudo apt-get update
sudo apt-get install build-essential openssl ssh expat libxyssl-dev libssl-dev
sudo apt-get remove subversion
sudo dpkg --purge subversion
wget http://subversion.tigris.org/downloads/subversion-1.5.4.tar.gz
wget http://subversion.tigris.org/downloads/subversion-deps-1.5.4.tar.gz
tar xvfz subversion-1.5.4.tar.gz
tar xvfz subversion-deps-1.5.4.tar.gz
cd subversion-1.5.4/neon/
./configure --prefix=/usr/local --with-ssl --with-pic
make
sudo make install
cd ..
rm -rf neon
./configure --prefix=/usr/local --with-ssl --with-neon=/usr/local
make
sudo make install
cd ..
rm -rf subversion-1.5.4
rm subversion-1.5.4.tar.gz
rm subversion-deps-1.5.4.tar.gz
exit 0

```Hope this helps someone!

Aaron

---

