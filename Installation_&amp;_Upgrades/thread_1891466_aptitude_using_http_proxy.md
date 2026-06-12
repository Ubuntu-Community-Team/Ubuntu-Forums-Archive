---
title: "aptitude using http proxy"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by DaveE84 on 2011-12-05
Ubuntu server 10.04 LTS 
Linux xxx 3.0.4-linode38 #1 SMP Thu Sep 22 14:59:08 EDT 2011 i686 GNU/Linux 
Some time ago I setup apt to use a proxy using a /etc/apt/apt.conf.d/01proxy file.  It was an apt cache on the local network.  Lately the proxy hasn't been reliable so I decided to delete the 01proxy file.  After doing this however it appears apt is attempting to connect to the local host.  Here is some examples of the error I am getting:
> 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources 
  404  Not Found [IP: 2600:3c03::f03c:91ff:fe93:f238 80] 
 
W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)   404  Not Found [IP: 2600:3c03::f03c:91ff:fe93:f238 80]
2600:3c03::f03c:91ff:fe93:f238 is the link-local ipv6  address.  I can only guess it's still trying to use a proxy without an  address so it's using the local IP.  I don't have an apt.conf file.  I'm  at a loss of what to do here, I don't see anything that would tell apt  to use a proxy.
I can use lynx to connect to  [http://security.ubuntu.com](http://security.ubuntu.com) normally so it's not a DNS or firewall issue.
The only similar issues I've been able to find are related to people using programs such as tor or privoxy, neither of which I have or anything similar.  I am not sure if this is a bug or if I am doing something wrong.

Here is my sources file, I changed everything to FTP and that seems to be a workaround right now, however HTTP does not work:
> ## main & restricted repositories
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid main restricted

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-updates main restricted

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-security main restricted

## universe repositories - uncomment to enable
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid universe

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) lucid-security universeThis is my apt-config dump
> APT ""; 
APT::Architecture "i386"; 
APT::Build-Essential ""; 
APT::Build-Essential:: "build-essential"; 
APT::Install-Recommends "false"; 
APT::Install-Suggests "0"; 
APT::Acquire ""; 
APT::Acquire::Translation "environment"; 
APT::NeverAutoRemove ""; 
APT::NeverAutoRemove:: "^linux-firmware$"; 
APT::NeverAutoRemove:: "^linux-image.*"; 
APT::NeverAutoRemove:: "^linux-restricted-modules.*"; 
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*"; 
APT::Never-MarkAuto-Sections ""; 
APT::Never-MarkAuto-Sections:: "metapackages"; 
APT::Never-MarkAuto-Sections:: "restricted/metapackages"; 
APT::Never-MarkAuto-Sections:: "universe/metapackages"; 
APT::Never-MarkAuto-Sections:: "multiverse/metapackages"; 
APT::Never-MarkAuto-Sections:: "oldlibs"; 
APT::Never-MarkAuto-Sections:: "restricted/oldlibs"; 
APT::Never-MarkAuto-Sections:: "universe/oldlibs"; 
APT::Never-MarkAuto-Sections:: "multiverse/oldlibs"; 
Dir "/"; 
Dir::State "var/lib/apt/"; 
Dir::State::lists "lists/"; 
Dir::State::cdroms "cdroms.list"; 
Dir::State::mirrors "mirrors/"; 
Dir::State::userstatus "status.user"; 
Dir::State::status "/var/lib/dpkg/status"; 
Dir::Cache "var/cache/apt/"; 
Dir::Cache::archives "archives/"; 
Dir::Cache::srcpkgcache "srcpkgcache.bin"; 
Dir::Cache::pkgcache "pkgcache.bin"; 
Dir::Etc "etc/apt/"; 
Dir::Etc::sourcelist "sources.list"; 
Dir::Etc::sourceparts "sources.list.d"; 
Dir::Etc::vendorlist "vendors.list"; 
Dir::Etc::vendorparts "vendors.list.d"; 
Dir::Etc::main "apt.conf"; 
Dir::Etc::netrc "auth.conf"; 
Dir::Etc::parts "apt.conf.d"; 
Dir::Etc::preferences "preferences"; 
Dir::Etc::preferencesparts "preferences.d"; 
Dir::Bin ""; 
Dir::Bin::methods "/usr/lib/apt/methods"; 
Dir::Bin::dpkg "/usr/bin/dpkg"; 
Dir::Media ""; 
Dir::Media::MountPath "/media/apt"; 
Dir::Log "var/log/apt"; 
Dir::Log::Terminal "term.log"; 
Dir::Log::History "history.log"; 
aptitude ""; 
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$"; 
aptitude::Get-Root-Command "sudo:/usr/bin/sudo"; 
DPkg ""; 
DPkg::Pre-Install-Pkgs ""; 
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true"; This is the output of env:
> TERM=vt100
SHELL=/bin/bash
SSH_CLIENT=....
SSH_TTY=/dev/pts/0
USER=....
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
MAIL=/var/mail/....
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/...
LANG=en_US.UTF-8
SHLVL=1
HOME=/home/....
LOGNAME=....
SSH_CONNECTION=....
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

---

