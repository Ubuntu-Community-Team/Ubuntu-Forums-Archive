---
title: "How to find all packes using a shared lib?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by tinkertim on 2008-07-02
Hello,

I am about to make some changes to libreadline and libedit (aka libeditline), I need to try to find all installed packages that are dynamically linked against either library.

Is there some way I can use dpkg to find what installed programs depend on either library?

Thanks in advance :)

---

### Post by scragar on 2008-07-02
```
Package: libreadline5

Reverse Depends: 
  smbclient,libreadline5 5.2
  samba-common,libreadline5 5.2
  libreadline-ruby1.8,libreadline5 5.2
  smbclient,libreadline5 5.2
  samba-common,libreadline5 5.2
  quagga,libreadline5 5.2
  postgresql-client-8.3,libreadline5 5.2
  parted,libreadline5 5.2
  mysql-server-5.0,libreadline5 5.2
  mysql-client-5.0,libreadline5 5.2
  gdb,libreadline5 5.2
  zssh,libreadline5 5.2
  zephyr-server-krb,libreadline5 5.2
  zephyr-server,libreadline5 5.2
  zephyr-clients,libreadline5 5.2
  ytree,libreadline5 5.1
  ysm,libreadline5 5.2
  yaz,libreadline5 5.1
  yafc,libreadline5 5.2
  xulrunner,libreadline5 5.2
  xtell,libreadline5 5.2
  xqf,libreadline5 5.2
  xine-ui,libreadline5 5.2
  xindy,libreadline5 5.2
  wflogs,libreadline5 5.2
  wcalc,libreadline5 5.2
  verilog,libreadline5 5.2
  units,libreadline5 5.2
  uml-utilities,libreadline5 5.2
  udftools,libreadline5 5.2
  tomoyo-ccstools,libreadline5 5.2
  timemachine,libreadline5 5.2
  teg,libreadline5 5.2
  tdl,libreadline5
  tclreadline,libreadline5 5.2
  swi-prolog,libreadline5 5.2
  steptalk,libreadline5 5.2
  sqsh,libreadline5 5.1
  sqlrelay,libreadline5 5.2
  spl-webspl,libreadline5 5.2
  spl-core,libreadline5 5.2
  spidermonkey-bin,libreadline5 5.2
  socat,libreadline5 5.2
  shogun-readline,libreadline5 5.2
  sdcv,libreadline5 5.1
  scm,libreadline5 5.2
  scli,libreadline5 5.2
  scanmem,libreadline5 5.2
  rpncalc,libreadline5 5.2
  rplay-client,libreadline5 5.2
  rlwrap,libreadline5 5.2
  rlfe,libreadline5 5.2
  rhyme,libreadline5 5.1
  renameutils,libreadline5 5.2
  remake,libreadline5 5.2
  rcalc,libreadline5 5.2
  rc,libreadline5 5.1
  ratpoison,libreadline5 5.2
  r-base-core,libreadline5 5.2
  qalc,libreadline5 5.2
  pypy-stackless,libreadline5 5.2
  pypy,libreadline5 5.2
  pwsafe,libreadline5 5.2
  postgresql-client-8.2,libreadline5 5.2
  plptools,libreadline5 5.2
  pinfo,libreadline5 5.1
  pilot-link,libreadline5 5.2
  piklab,libreadline5 5.2
  parrot,libreadline5 5.2
  pari-gp,libreadline5 5.2
  pal,libreadline5
  openwince-jtag,libreadline5 5.2
  omake,libreadline5 5.2
  octplot,libreadline5 5.2
  octaviz,libreadline5 5.2
  octave3.0,libreadline5 5.2
  octave-sp,libreadline5 5.2
  octave-pfstools,libreadline5 5.2
  nyquist,libreadline5
  nwall,libreadline5 5.2
  nmzmail,libreadline5 5.2
  nickle,libreadline5 5.2
  mutella,libreadline5 5.2
  muse,libreadline5 5.2
  muscletools,libreadline5 5.2
  mrbayes,libreadline5 5.2
  mn-fit,libreadline5 5.2
  midish,libreadline5 5.2
  medussa,libreadline5 5.2
  mdk,libreadline5 5.2
  mcvs,libreadline5 5.2
  maxima,libreadline5 5.2
  mathomatic,libreadline5 5.2
  maria,libreadline5
  mailutils,libreadline5 5.2
  lustre-utils,libreadline5 5.2
  lush,libreadline5 5.2
  lua5.1,libreadline5 5.2
  lsh-utils,libreadline5 5.2
  lsh-server,libreadline5 5.2
  linphone-nox,libreadline5 5.2
  lie,libreadline5 5.2
  libzephyr3-krb,libreadline5 5.2
  libxbsql-bin,libreadline5 5.2
  libterm-readline-gnu-perl,libreadline5 5.1
  librep9,libreadline5 5.2
  libreadline-ruby1.9,libreadline5 5.2
  libreadline-ruby1.8,libreadline5 5.2
  libparrot0.4.13,libreadline5 5.2
  liblash2,libreadline5 5.2
  libgda3-bin,libreadline5 5.2
  libgda2-bin,libreadline5 5.2
  libfluidsynth1,libreadline5 5.2
  ldapvi,libreadline5 5.2
  lashd,libreadline5 5.2
  lash-bin,libreadline5 5.2
  ladcca-bin,libreadline5
  ktechlab,libreadline5 5.2
  kst-bin,libreadline5 5.2
  kaya,libreadline5 5.2
  kalgebra-kde4,libreadline5 5.2
  jackd,libreadline5 5.2
  isdneurofile,libreadline5 5.2
  ipmitool,libreadline5 5.2
  inetutils-ftp,libreadline5 5.2
  illuminator-demo,libreadline5 5.2
  id3ed,libreadline5 5.2
  icestorm,libreadline5 5.2
  icegrid,libreadline5 5.2
  hugs,libreadline5 5.2
  honeyd,libreadline5 5.2
  hol88,libreadline5 5.2
  hoichess,libreadline5 5.2
  hmake,libreadline5 5.2
  helium,libreadline5 5.2
  hat,libreadline5 5.2
  gwave,libreadline5 5.2
  guile-1.8-libs,libreadline5 5.2
  gretl,libreadline5 5.2
  grass,libreadline5 5.2
  gpsim,libreadline5 5.2
  gphoto2,libreadline5 5.2
  gnupg2,libreadline5 5.2
  gnudatalanguage,libreadline5 5.2
  gnuchess,libreadline5 5.1
  gnucap,libreadline5 5.2
  gnubg,libreadline5 5.2
  gnu-smalltalk,libreadline5 5.2
  gnome-genius,libreadline5 5.2
  gnat-gdb,libreadline5 5.2
  git,libreadline5 5.2
  ginac-tools,libreadline5 5.2
  ghc6,libreadline5 5.2
  ggz-txt-client,libreadline5 5.2
  gftp-text,libreadline5 5.2
  genius-common,libreadline5 5.2
  genius,libreadline5 5.2
  gclcvs,libreadline5 5.2
  gcl,libreadline5 5.2
  fvwm,libreadline5 5.2
  fuzz,libreadline5 5.2
  ftp-ssl,libreadline5 5.1
  freetalk,libreadline5 5.2
  freesci,libreadline5 5.2
  freeciv-server,libreadline5 5.2
  fityk,libreadline5 5.2
  evolver,libreadline5 5.2
  evms-cli,libreadline5 5.2
  escputil,libreadline5 5.2
  es,libreadline5 5.1
  empire-lafe,libreadline5 5.1
  ecasound,libreadline5 5.2
  dump,libreadline5 5.2
  devtodo,libreadline5 5.2
  dbacl,libreadline5 5.2
  cyphesis-cpp-clients,libreadline5 5.2
  ctsim,libreadline5 5.2
  ctrlproxy,libreadline5 5.2
  coldfire,libreadline5
  clisp,libreadline5 5.2
  cle,libreadline5
  cl-readline,libreadline5 5.2
  chrony,libreadline5 5.2
  cgdb,libreadline5 5.2
  cdecl,libreadline5
  cdcd,libreadline5 5.2
  cadaver,libreadline5 5.2
  bird,libreadline5 5.2
  bible-kjv,libreadline5 5.1
  bibindex,libreadline5 5.2
  axiom,libreadline5 5.2
  avrdude,libreadline5 5.2
  atftp,libreadline5 5.2
  asymptote,libreadline5 5.2
  aptsh,libreadline5 5.2
  apcalc,libreadline5 5.2
  apachetop,libreadline5 5.2
  amule-utils,libreadline5 5.2
  amule-daemon,libreadline5 5.2
  amiga-fdisk-cross,libreadline5 5.1
  amanda-server,libreadline5 5.2
  amanda-common,libreadline5 5.2
  amanda-client,libreadline5 5.2
  afterstep,libreadline5 5.2
  afflib,libreadline5 5.1
  adesklets,libreadline5 5.2
  acl2,libreadline5 5.2
  abook,libreadline5 5.2
  xtrs,libreadline5 5.2
  vice,libreadline5 5.2
  spectemu-x11,libreadline5 5.2
  octave-gpc,libreadline5 5.2
  xfsprogs,libreadline5 5.2
  wpasupplicant,libreadline5 5.2
  unixodbc,libreadline5 5.2
  sqlite3,libreadline5 5.2
  sqlite,libreadline5 5.2
  smbclient,libreadline5 5.2
  samba-common,libreadline5 5.2
  reiser4progs,libreadline5 5.2
  readline-common,libreadline5 5.0-11
  readline-common,libreadline5 5.0-11
  quagga,libreadline5 5.2
  python2.5-dbg,libreadline5 5.2
  python2.5,libreadline5 5.2
  python2.4-dbg,libreadline5 5.2
  python2.4,libreadline5 5.2
  postgresql-client-8.3,libreadline5 5.2
  parted,libreadline5 5.2
  ocfs2-tools,libreadline5 5.2
  ntp,libreadline5 5.2
  mysql-server-5.0,libreadline5 5.2
  mysql-client-5.0,libreadline5 5.2
  multipath-tools,libreadline5 5.2
  mdbtools,libreadline5 5.2
  malaga-bin,libreadline5 5.2
  lvm2,libreadline5 5.2
  lua50,libreadline5 5.2
  libzephyr3,libreadline5 5.2
  libxml2-utils,libreadline5 5.2
  libvirt-bin,libreadline5 5.2
  libreadline5-dev,libreadline5 5.2-3build1
  libreadline5-dbg,libreadline5 5.2-3build1
  libreadline-java,libreadline5 5.2
  lftp,libreadline5 5.2
  kexi,libreadline5 5.2
  hunspell,libreadline5 5.2
  guile-1.6-libs,libreadline5 5.2
  gpgsm,libreadline5 5.2
  gnupg,libreadline5 5.2
  gdb,libreadline5 5.2
  ftp,libreadline5 5.2
  clvm,libreadline5 5.2
  bc,libreadline5 5.2
  abiword-plugins,libreadline5 5.2

``````
Package: libeditline0
Reverse Depends: 
  libeditline-dev,libeditline0 1.12-5
  firebird2.0-super,libeditline0
  firebird2.0-classic,libeditline0

```


I don't know how to limit this to just installed programs though :(

EDIT:

for what you want use:

```
apt-cache --installed rdepends libreadline5
```
AND
```
apt-cache --installed rdepends libeditline0
```

---

### Post by iaculallad on 2008-07-02
Try using the **ldd** terminal command:

The example below will list (verbose) all shared libraries being used by the **gedit** application.

*Just be sure that you're in the /usr/bin directory when executing this command.

```
ldd -v gedit
```

or

```
ldd -v /usr/bin/gedit
```

---

### Post by tinkertim on 2008-07-02
> **iaculallad said:**
> Try using the **ldd** terminal command:

The example below will list (verbose) all shared libraries being used by the **gedit** application.

*Just be sure that you're in the /usr/bin directory when executing this command.

```
ldd -v gedit
```

or

```
ldd -v /usr/bin/gedit
```

ldd gives me great info if I want to build a chroot. In fact, it also helps determine programs that were compiled with bloated shared dependencies.

Unfortunately, it doesn't tell me every installed program on the system that depends on some shared lib. :(

I'm going to be hacking at a few (readline being one) and I'm hoping to find out what I might break. I've done testing in /usr/local/lib, now its time to see what shatters :)

---

### Post by tinkertim on 2008-07-02
> **scragar said:**
> 

EDIT:

for what you want use:

```
apt-cache --installed rdepends libreadline5
```
AND
```
apt-cache --installed rdepends libeditline0
```

That worked!! Thank you scragar :) I really needed to see what I (might) break when testing in production.

---

### Post by tinkertim on 2008-07-02
I also need to say, this forum is the best :) I've been using Ubuntu since its first release .. when my day job is not so taxing I hope to answer more questions than I ask.

---

