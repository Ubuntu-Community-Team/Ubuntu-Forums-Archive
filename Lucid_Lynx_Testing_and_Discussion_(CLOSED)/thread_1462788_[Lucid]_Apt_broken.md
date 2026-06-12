---
title: "[Lucid] Apt broken"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Balachmar on 2010-04-26
Hi can someone help me fix my apt?

I get the following error:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu6) but 2.11.1-0ubuntu7 is installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7) but 2.11.1-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.

```

I have already tried the -f option which does not help.
result:
```

debconf: Perl may be unconfigured (Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 203163 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu6 (using .../libc6_2.11.1-0ubuntu7_i386.deb) ...
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how to fix this?
This started last wednesday.

---

### Post by wilee-nilee on 2010-04-26
I forget the command but try and open synaptic and it will probably give the command you need to run. If synaptic does open look in the broken packages area.

---

### Post by Balachmar on 2010-04-26
> **wilee-nilee said:**
> I forget the command but try and open synaptic and it will probably give the command you need to run. If synaptic does open look in the broken packages area.
Sorry, forgot to mention. Alread tried that, the message from that dialog is similar to the ones posted above.

---

### Post by dino99 on 2010-04-26
sudo dpkg-reconfigure libc6
sudo dpkg-reconfigure libc6-i686
sudo dpkg-reconfigure libc6-dev

---

### Post by Balachmar on 2010-04-26
> **dino99 said:**
> sudo dpkg-reconfigure libc6
sudo dpkg-reconfigure libc6-i686
sudo dpkg-reconfigure libc6-dev
result for each of those commands:
sudo dpkg-reconfigure libc6
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/sbin/dpkg-reconfigure line 9.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9.

---

### Post by dino99 on 2010-04-26
> **Balachmar said:**
> result for each of those commands:
sudo dpkg-reconfigure libc6
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/sbin/dpkg-reconfigure line 9.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9.

ah ok Db.pm is corrupted, so rename it

then check your repo into synaptic: you might have only "lucid" repos and comment all third party and ppa, update & sudo apt-get install -f & upgrade

if there is still problems: sudo dpkg --configure -a

---

### Post by Balachmar on 2010-04-26
> **dino99 said:**
> ah ok Db.pm is corrupted, so rename it

then check your repo into synaptic: you might have only "lucid" repos and comment all third party and ppa, update & sudo apt-get install -f & upgrade

if there is still problems: sudo dpkg --configure -a
That also does not work:
Now the various commands complain about Db.pm not being available.
```

sudo dpkg --configure -a
Setting up man-db (2.5.7-2) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.11.1-0ubuntu7); however:
  Version of libc6 on system is 2.11.1-0ubuntu6.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-mscorefonts-installer (3.2) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up aspell-nl (1:1.10-5) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
Error running aspell-autobuildhash
dpkg: error processing aspell-nl (--configure):
 subprocess installed post-installation script returned error exit status 25
Errors were encountered while processing:
 man-db
 libc6-dev
 ttf-mscorefonts-installer
 aspell-nl

```

---

### Post by klemes on 2010-04-26
I think you are heading full-speed for a re-install here....

But wait a little longer if someone has any better suggestions though  through the years I've found that libc6-related apt-get errors are not recoverable....at least by me....:):popcorn:
Good Luck!!!!!!!!!!!!:guitar:


Just out of curiosity is your system fully operational at this stage...?
I bet it won't be if you reboot....
Sorry but I've been through that recently.....:(

Good luck in any case!!!!!

---

### Post by Balachmar on 2010-04-26
> **klemes said:**
> I think you are heading full-speed for a re-install here....

But wait a little longer if someone has any better suggestions though  through the years I've found that libc6-related apt-get errors are not recoverable....at least by me....:):popcorn:
Good Luck!!!!!!!!!!!!:guitar:


Just out of curiosity is your system fully operational at this stage...?
I bet it won't be if you reboot....
Sorry but I've been through that recently.....:(

Good luck in any case!!!!!
Well, the system is perfectly functional, even rebooting works fine. it is just that I cannot update my system... (Which is ofcourse crucial)
Somehow I think it has more to do with Perl, however I cannot seem to get rid of that corrupted file. Even installed the perl debs using dpkg -i does not seem to replace the Db.pm file.
Any idea how I can get that file (and all perl related files fixed/reinstalled)
That should be possible right?

---

### Post by klemes on 2010-04-26
Well it seems your case is not as terminal as mine proved to be.....:)

Maybe try aptitude instead???

I doubt it it will be any different but these will give you some alternative scenarios at least.One of them could be acceptable...you never know...:)

---

### Post by Balachmar on 2010-04-26
> **klemes said:**
> Well it seems your case is not as terminal as mine proved to be.....:)

Maybe try aptitude instead???

I doubt it it will be any different but these will give you some alternative scenarios at least.One of them could be acceptable...you never know...:)

Already tried that, same results (as expected)

---

### Post by klemes on 2010-04-26
I am talking about 

```
sudo aptitude -f install
```

---

### Post by Balachmar on 2010-04-26
> **klemes said:**
> I am talking about 

```
sudo aptitude -f install
```
Just to be sure to output:
```

sudo aptitude -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  libc6 libc6-i686 
The following partially installed packages will be configured:
  aspell-nl libc6-dev man-db ttf-mscorefonts-installer 
2 packages upgraded, 0 newly installed, 0 to remove and 114 not upgraded.
Need to get 0B/5,007kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
debconf: Perl may be unconfigured (Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 203163 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu6 (using .../libc6_2.11.1-0ubuntu7_i386.deb) ...
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.5.7-2) ...
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.11.1-0ubuntu7); however:
  Version of libc6 on system is 2.11.1-0ubuntu6.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-mscorefonts-installer (3.2) ...
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up aspell-nl (1:1.10-5) ...
Unrecognized character \xDE in column 1 at /usr/share/perl5/Debconf/Db.pm line 1.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
Error running aspell-autobuildhash
dpkg: error processing aspell-nl (--configure):
 subprocess installed post-installation script returned error exit status 25
Errors were encountered while processing:
 man-db
 libc6-dev
 ttf-mscorefonts-installer
 aspell-nl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by klemes on 2010-04-26
I gather that you have checked already if it is a fully populated /(root) partition.If not check with fd -h.
Also check your apt repository sources and uncheck everything except official LucidLynx repos then run through the apt-get update / upgrade routine again.:popcorn:

Yours of course seems a very peculiar error.
For the record I had destroyed a perfectly good running 8.04 Hardy installation when upgraded libc6 using Karmic repos.
Have you 've done anything peculiar with your repos lately?????:guitar:

---

### Post by dino99 on 2010-04-26
erased

---

### Post by Balachmar on 2010-04-26
> **klemes said:**
> I gather that you have checked already if it is a fully populated /(root) partition.If not check with fd -h.
Also check your apt repository sources and uncheck everything except official LucidLynx repos then run through the apt-get update / upgrade routine again.:popcorn:

Yours of course seems a very peculiar error.
For the record I had destroyed a perfectly good running 8.04 Hardy installation when upgraded libc6 using Karmic repos.
Have you 've done anything peculiar with your repos lately?????:guitar:
Well I think it has something to do with my perl installation, but I cannot find the package responsible for creating /usr/share/perl5/Debconf/Db.pm

---

### Post by Balachmar on 2010-04-26
> **dino99 said:**
> here is my /usr/share/debconf/frontend:

```
#!/usr/bin/perl -w
# This file was preprocessed, do not edit!


use strict;
use Debconf::Db;
use Debconf::Template;
use Debconf::AutoSelect qw(:all);
use Debconf::Log qw(:all);

Debconf::Db->load;

debug developer => "frontend started";

my $frontend=make_frontend();

shift @ARGV if $ARGV[0] eq '--';

my $package;
if ($ENV{DEBCONF_PACKAGE}) {
	$package=$ENV{DEBCONF_PACKAGE};
}
elsif ($ARGV[0]=~m!^.*/(.*?)\.(?:postinst|postrm|prerm)$!) {
	$package=$1;
}
elsif (-e "/var/lib/dpkg/tmp.ci/control") {
	open (CONTROL, "< /var/lib/dpkg/tmp.ci/control")
		|| die "Debconf: unable to open control file: $!";
	while (<CONTROL>) {
		if (/^Package: (.*)/) {
			$package=$1;
			last;
		}
	}
	close CONTROL;
	if (! exists $ENV{PERL_DL_NONLAZY} || ! $ENV{PERL_DL_NONLAZY}) {
		warn "PERL_DL_NONLAZY is not set, if debconf is running from a preinst script, this is not safe";
	}
}
else {
	$package='';

	debug developer => 'Trying to find a templates file..';
	sub trytemplate {
		my $fn=shift;
		debug developer => "Trying $fn";
		if (-e $fn) {
			debug developer => "I guess it is $fn";
			Debconf::Template->load($fn, $package);
			return 1;
		}
		else {
			return;
		}
	}

	unless (trytemplate("$ARGV[0].templates")) {
		unless ($ARGV[0]=~m/(.*)config$/ && trytemplate("${1}templates")) {
			unless ($ARGV[0]=~m!^(?:.*/)?(.*)! && trytemplate("/usr/share/debconf/templates/${1}.templates")) {
				debug developer => "Couldn't find a templates file."
			}
		}
	}
}
debug developer => "frontend running, package name is $package";
$frontend->default_title($package) if length $package;
$frontend->info(undef);

if ($ARGV[0] =~/^(.*[.\/])(?:postinst|preinst)$/) {
	my $base=$1;

	my $templates=$base."templates";
	Debconf::Template->load($templates, $package)
		if -e $templates;

	my $config=$base."config";
	if (-e $config) {
		my $version=$ARGV[2];
		if (! defined($version)) {
			$version='';
		}
		my $confmodule=make_confmodule($config,
			"configure", $version);

		$confmodule->owner($package);

		1 while ($confmodule->communicate);
		
		exit $confmodule->exitcode if $confmodule->exitcode > 0;
	}
}

my $confmodule=make_confmodule(@ARGV);

$confmodule->owner($package);

1 while ($confmodule->communicate);

$frontend->shutdown;

Debconf::Db->save;

exit $confmodule->exitcode;

```
Could you maybe post the /usr/share/perl5/Debconf/Db.pm file?

---

### Post by dino99 on 2010-04-26
as that file is : This file was preprocessed, do not edit!

i wonder if reinstalling the kernel could rewrite it

---

### Post by dino99 on 2010-04-26
off

---

### Post by Balachmar on 2010-04-26
> **dino99 said:**
> as that file is : This file was preprocessed, do not edit!

i wonder if reinstalling the kernel could rewrite it

I now know from which package that came: debconf.
So I downloaded the debconf deb (using synaptic and installed it myself using dpkg. And now it seems as though everything is updating again.

---

### Post by klemes on 2010-04-26
> **Balachmar said:**
> Well I think it has something to do with my perl installation, but I cannot find the package responsible for creating /usr/share/perl5/Debconf/Db.pm


For this you can install apt-file: sudo apt-get install apt-file.

Stupid of me at this moment you cannot install anything I forgot.
But maybe someone else with a Lucid installation (I am not at this moment in front of one)can install it and search in which package exectly the DB.pm file resides with:

sudo apt-file update && sudo apt-file search DB.pm

:guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by klemes on 2010-04-26
> **Balachmar said:**
> I now know from which package that came: debconf.
So I downloaded the debconf deb (using synaptic and installed it myself using dpkg. And now it seems as though everything is updating again.
Excellent!!!!!!!!!!!!!!!!!!!!!!:popcorn:
:guitar:

---

### Post by dino99 on 2010-04-26
> **Balachmar said:**
> I now know from which package that came: debconf.
So I downloaded the debconf deb (using synaptic and installed it myself using dpkg. And now it seems as though everything is updating again.

yeah always try the simplest way, but now we have learn something more  :P

---

