---
title: "Update to FreeRADIUS+EAP/PEAP-HowTo"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2010-08-07
It would be great to have an update to [this]("http://ubuntuforums.org/showthread.php?t=478804") How-To on building freeradius with EAP/PEAP support. The How-To was written for 7.04.

Building the server yourself gets around the problem that the rlm_eap_tls.so library is not included in the binary distribution, rendering the server useless for any up-to-date network. 

I can offer some insight, although my progress is blocked by an error for which no useful error message information is given at all. This is par for the course. Building from source almost never works. But perhaps your machine's configuration more closely resembles that of the developers for whom this build presumably does work. 

Perhaps a few of us working together can figure this out.


In "STEP 2" of the How-To,

The rules file evidently has changed since 7.04. I re-interpreted the editing instructions as follows:

```
	./configure \
		$(confflags) \
		--prefix=/usr \
		--exec-prefix=/usr \
		--mandir=$(mandir) \
		--sysconfdir=/etc \
		--libdir=$(libdir) \
		--datadir=/usr/share \
		--localstatedir=/var \
		--with-raddbdir=$(raddbdir) \
		--with-logdir=/var/log/$(package) \
		--enable-ltdl-install=no --enable-strict-dependencies \
		--with-large-files --with-udpfromto --with-edir \
		--enable-developer \
		--config-cache \
		--with-rlm_sql_postgresql_lib_dir=$(libdir) \
		--with-rlm_sql_postgresql_lib_dir=`pg_config --libdir` \
		--with-rlm_sql_postgresql_include_dir=`pg_config --includedir` \
		--with-system-libtool
#		--without-rlm_eap_tls \
#		--without-rlm_eap_ttls \
#		--without-rlm_eap_peap \
#		--without-rlm_otp \
#		--without-openssl \

```
Comment out options and move them beyond the end of the statement as shown. Add sql_postgresql to the modulelist statement, as in the original instructions. (Statement is near beginning of rules file now.)

Edit the control file, adding  libssl-dev, libpq-dev, as in the original.

The original instructions say  
```
# cd ~/build_freeradius/freeradius-1.1.3/debian
# cat control.postgresql >> control

```
I ignored this as the file control.postgresql does not exist. 
(Perhaps this is why my build fails. Any ideas what to do?)

```
# apt-get install libssl-dev libpq-dev
```

Edit the changelog file if you like.

Then, run 

```
# cd ~/build_freeradius
# apt-src build freeradius

```


**My results:**

After a lengthy process, building many files, I get this:

make: *** [install-arch] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
E: Building failed

What's wrong? Who can tell? (debian/rules is not a binary!)

---

