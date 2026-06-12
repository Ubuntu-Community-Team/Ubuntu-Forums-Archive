---
title: "&quot;Error Counter broken &gt; 0&quot; and other errors"
date: 2017-11-20
forum: Installation &amp; Upgrades
---

### Post by aleddilwynfisher on 2017-11-20
Hi guys, 

I've been getting numerous error messages every time I try to update, and everything I try seems to lead to a new error message. 

Originally, it kept saying I didn't have enough free space, which is ridiculous - I barely use any of the disk space on the computer. I tried all the various fixes suggested on these forums for that issue. 

The current error message I've been dealing with is the "Error Counter broken > 0" one discussed at [https://askubuntu.com/questions/263460/what-does-error-broken-count-0-mean](https://askubuntu.com/questions/263460/what-does-error-broken-count-0-mean)

I've tried various suggestions from that threat, most recently "sudo apt-get install --fix-broken," which got the following (as you will no doubt see, I use Ubuntu in Norwegian and it won't let me change back to English at the moment because of the errors, it seems; most of the relevant info below is in English though): 
```

aled@aled-Inspiron-15-3552:~$ sudo apt-get install --fix-broken
[sudo] passord for aled: 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold        
Leser tilstandsinformasjon ... Ferdig 
Retter på avhengighetsforhold ... Utført
Følgende pakker ble automatisk installert og er ikke lenger påkrevet:
  libmircommon5 linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
  linux-headers-4.4.0-75 linux-headers-4.4.0-75-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-97
  linux-headers-4.4.0-97-generic linux-image-4.4.0-72-generic
  linux-image-4.4.0-75-generic linux-image-4.4.0-77-generic
  linux-image-4.4.0-78-generic linux-image-4.4.0-79-generic
  linux-image-4.4.0-81-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-89-generic linux-image-4.4.0-93-generic
  linux-image-4.4.0-97-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-image-extra-4.4.0-77-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-89-generic linux-image-extra-4.4.0-93-generic
  linux-image-extra-4.4.0-97-generic snap-confine
Bruk «sudo apt autoremove» for å fjerne dem.
Følgende ekstra pakker vil bli installert:
  linux-image-4.4.0-93-generic linux-image-4.4.0-97-generic
  linux-image-4.4.0-98-generic
Foreslåtte pakker:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
Følgende NYE pakker vil bli installert:
  linux-image-4.4.0-93-generic linux-image-4.4.0-97-generic
  linux-image-4.4.0-98-generic
0 oppgraderte, 3 nylig installerte, 0 å fjerne og 265 ikke oppgradert.
28 pakker ikke fullt installert eller fjernet.
Må hente 0 B/65,8 MB med arkiver.
Etter denne operasjonen vil 201 MB ekstra diskplass bli brukt.
Vil du fortsette? [J/n] j
(Leser database ... 594182 filer og kataloger er for øyeblikket installerte.)
Preparing to unpack .../linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
Done.
Unpacking linux-image-4.4.0-98-generic (4.4.0-98.121) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-98-generic' to '/boot/System.map-4.4.0-98-generic.dpkg-new': klarte ikke å skrive (Ikke mer plass på enheten)
Ingen apport-rapport skrevet fordi feilmeldingen indikerer en «full disk»-feil
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
Preparing to unpack .../linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Done.
Unpacking linux-image-4.4.0-93-generic (4.4.0-93.116) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-4.4.0-93-generic' to '/boot/abi-4.4.0-93-generic.dpkg-new': klarte ikke å skrive (Ikke mer plass på enheten)
Ingen apport-rapport skrevet fordi feilmeldingen indikerer en «full disk»-feil
                                                                              dpkg-deb: feil: subprocess lim inn was killed by signal (Røret ble brutt)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Preparing to unpack .../linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Done.
Unpacking linux-image-4.4.0-97-generic (4.4.0-97.120) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-97-generic' to '/boot/vmlinuz-4.4.0-97-generic.dpkg-new': klarte ikke å skrive (Ikke mer plass på enheten)
Ingen apport-rapport skrevet fordi feilmeldingen indikerer en «full disk»-feil
                                                                              dpkg-deb: feil: subprocess lim inn was killed by signal (Røret ble brutt)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Det oppsto feil ved behandling av:
 /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



Let me know if you need any of that translated but, like I say, most of the stuff is also in English. 

Is there anyone who can help? I've had so many problems and I'm at the end of my tether with Ubuntu generally; I really have no idea why it is so difficult to just update the software. 

Cheers, 
Aled

---

### Post by VMC on 2017-11-20
So what about your repositories? "/etc/apt/sources.list". When you do "sudo apt update" what errors come out?

---

### Post by deadflowr on 2017-11-20
The gist of it is you need to clear out those old packages it listed.
(Those old linux-hearders and linux-image packages)

Their eating your disk space and that's what's causing the issue.
You might try running the autoremove command first, if that fails try a more manual approach by trying to remove just one kernel; at first.
use
```
sudo apt-get autoremove
```
if it fails try another approach.
first locate the version currently in use
```
uname -r
```
then run
```
sudo dpkg --purge linux-image-4.4.0-XX-generic linux-image-extra-4.4.0-XX-generic
```
change the XX to any of the numbered version from the list, that you are not currently running.
(Match both packages with the same XX version, if that makes sense.)
I would go with the -75 kernel.

If that runs without issues, then re-try the autoremove command and see if that runs without issues.

Hope it make sense.

---

### Post by photonxp on 2017-11-21
@[[COLOR=#000000]aleddilwynfisher[/COLOR]]("https://ubuntuforums.org/member.php?u=2029614")

Can you use Google translate to translate the "[COLOR=#000000][FONT=&quot]install --fix-broken[/FONT][/COLOR]" messages so that it's easier to get a general idea.

What's the result of this command?
sudo df -h

---

### Post by aleddilwynfisher on 2017-11-21
Hi! 

I tried the "autoremove" command and got the following (was in Norwegian, have put it through Google Translate): 

```
You may want to run "apt-get -f install" to correct this. The following packages have unrelated addictions:
 linux-image-extra-4.4.0-93-generic: Depends on: linux-image-4.4.0-93-generic but is not installed
 linux-image-extra-4.4.0-97-generic: Depends on: linux-image-4.4.0-97-generic but is not installed
 linux-image-extra-4.4.0-98-generic: Depends on: linux-image-4.4.0-98-generic but not installed
 linux-image-generic: Depends on: linux-image-4.4.0-98-generic but is not installed
E: Untimely Dependence - Try "-f"
```

This thing about "unrelated addictions" (this is an example of poor Google Translating - I think "unrelated dependencies" is probably nearer the real meaning) is something I see a lot. 

I don't really understand what I'm supposed to replace the 'XXs' with in your example - could you explain how I find this out? The response to uname -r was: 4.4.0-87-generic.

Many thanks and best wishes, 
Aled

I got the following messages (again, run through Google Translate) at the end of "sudo apt-get update": 

```
W: Packaging "http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release" is missing the release file. N: Data from this type of packet store can not be authenticated, and it is therefore considered dangerous to use them.
N: For apt-secure (8), read manual (man-page) for detailed info about creating packet layers and user setup.
W: An error occurred during signature verification. Package storage is not updated, and previous index files are now being used. GPG Error Message: [http://repository.spotify.com](http://repository.spotify.com) Stack InRelease: The following signatures could not be verified because the public key is unavailable: NO_PUBKEY EFDC8610341D9410
W: Failed to obtain [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease) The following signatures could not be verified because the public key is unavailable: NO_PUBKEY EFDC8610341D9410
E: Failed to obtain [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages) 404 Not Found
W: Some index files were not downloaded. They have either been ignored or replaced with old index files
```

I received this response to "sudo df -h":

```
Filsystem                   Størrelse Brukt Tilgj. Bruk% Montert på
udev                             1,9G     0   1,9G    0% /dev
tmpfs                            387M   11M   376M    3% /run
/dev/mapper/ubuntu--vg-root      454G   73G   359G   17% /
tmpfs                            1,9G  632K   1,9G    1% /dev/shm
tmpfs                            5,0M  4,0K   5,0M    1% /run/lock
tmpfs                            1,9G     0   1,9G    0% /sys/fs/cgroup
/dev/sda1                        472M  461M      0  100% /boot
tmpfs                            387M   56K   387M    1% /run/user/1000
/home/aled/.Private              454G   73G   359G   17% /home/aled
```

Filsystem = File system
Størrelse = Size
Brukt = Used
Tilgj. = Available
Montert på = Mounted on

---

### Post by deadflowr on 2017-11-21
> I don't really understand what I'm supposed to replace the 'XXs' with in your example - could you explain how I find this out? The response to uname -r was: 4.4.0-87-generic.
Since you're running the 4.4.0-87-generic kernel, you can run the command I gave with these packages:
```
linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic 
```
notice I replaced the XX with the 72 version?
So run this:
```
sudo dpkg --purge linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
```
The reality is any of the listed linux-image/linux-image-extra version pairs that aren't the one listed from the uname -r output would do, but the 72 is the oldest so why not try removing that one first, if that make sense.

But overall that's only the start of you problems, if you get space cleaned up you'll need do some fixing of a couple apt problems.
The first is easy so start with that one.
The tualatrix ppa does not have a version for the 16.04 so that needs to be removed.
```
sudo add-apt-repository -r ppa:tualatrix/ppa
```

The second is something that comes along every once in a while from the spotify repository
Look at oldos2er's post here on what to do to fix that issue:
[https://ubuntuforums.org/showthread.php?t=2303314&p=13393435#post13393435]("https://ubuntuforums.org/showthread.php?t=2303314&p=13393435#post13393435")

Hope it makes sense

---

### Post by aleddilwynfisher on 2017-11-22
Thanks! I've tried all of that and then tried "sudo apt-get update" again, and this is what happened: 

```
aled@aled-Inspiron-15-3552:~$ sudo dpkg --purge linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
[sudo] passord for aled: 
(Leser database ... 594181 filer og kataloger er for øyeblikket installerte.)
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-72-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--purge):
 underprosessen installerte post-removal-skript returnerte feilstatus 1
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Lager grub-oppsettsfil …
Advarsel: Du kan ikke lenger gi «GRUB_TIMEOUT» en annen verdi enn null når «GRUB_HIDDEN_TIMEOUT» har en verdi.
Fant linux-bilde: /boot/vmlinuz-4.4.0-92-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-91-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-89-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-87-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-87-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-83-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-83-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-81-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-81-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-79-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-79-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-78-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-78-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-77-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-77-generic
Fant linux-bilde: /boot/vmlinuz-4.4.0-75-generic
Fant initrd-bilde: /boot/initrd.img-4.4.0-75-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
ferdig
Purging configuration files for linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Det oppsto feil ved behandling av:
 linux-image-extra-4.4.0-72-generic
aled@aled-Inspiron-15-3552:~$ sudo add-apt-repository -r ppa:tualatrix/ppa
 The official Ubuntu Tweak stable repository
 Mer informasjon: https://launchpad.net/~tualatrix/+archive/ubuntu/ppa
Trykk [ENTER] for å fortsette, eller ctrl+c for å avbryte fjerning

aled@aled-Inspiron-15-3552:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
Executing: /tmp/tmp.Gx6C5EwTv5/gpg.1.sh --keyserver
keyserver.ubuntu.com
--recv-keys
KEYID
gpg: «KEYID» er ikke en nøkkel-ID, og blir hoppet over

aled@aled-Inspiron-15-3552:~$ sudo apt-get update
Funnet:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hent:2 http://repository.spotify.com stable InRelease [3 302 B]                
Funnet:3 http://no.archive.ubuntu.com/ubuntu xenial InRelease                  
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease      
Funnet:5 http://no.archive.ubuntu.com/ubuntu xenial-updates InRelease
Funnet:6 http://no.archive.ubuntu.com/ubuntu xenial-backports InRelease
Feil:2 http://repository.spotify.com stable InRelease
  De følgende signaturene kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY EFDC8610341D9410
Funnet:7 http://dl.google.com/linux/chrome/deb stable Release
Hentet 3 302 B på 1s (2 722 B/s)               
Leser pakkelister ... Ferdig
W: Det oppstod en feil under signaturbekreftelse. Pakkelageret er ikke oppdatert, og tidligere indeksfiler blir nå brukt. GPG-feilmelding: http://repository.spotify.com stable InRelease: De følgende signaturene kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY EFDC8610341D9410
W: Klarte ikke å skaffe http://repository.spotify.com/dists/stable/InRelease  De følgende signaturene kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY EFDC8610341D9410
W: Noen indeksfiler ble ikke lastet ned. De har enten blitt ignorert eller erstattet med gamle indeksfiler.

aled@aled-Inspiron-15-3552:~$ ls /etc/apt/sources.list.d/
google-chrome.list       spotify.list.save
google-chrome.list.save  tualatrix-ubuntu-ppa-xenial.list
spotify.list             tualatrix-ubuntu-ppa-xenial.list.save
aled@aled-Inspiron-15-3552:~$ 
```

Some translations (I still can't switch languages): Advarsel: Du kan ikke lenger gi «GRUB_TIMEOUT» en annen verdi enn null når «GRUB_HIDDEN_TIMEOUT» har en verdi.
Warning: You can no longer give "GRUB_TIMEOUT" a value other than zero when "GRUB_HIDDEN_TIMEOUT" has a value.

gpg: «KEYID» er ikke en nøkkel-ID, og blir hoppet over
gpg: "KEYID" is not a key ID and is skipped

De følgende signaturene kunne ikke verifiseres fordi den offentlige nøkkelen ikke er tilgjengelig: NO_PUBKEY EFDC8610341D9410
The following signatures could not be verified because the public key is unavailable: NO_PUBKEY EFDC8610341D9410

W: Det oppstod en feil under signaturbekreftelse. Pakkelageret er ikke 
oppdatert, og tidligere indeksfiler blir nå brukt. GPG-feilmelding: 
[http://repository.spotify.com](http://repository.spotify.com) stable InRelease: De følgende signaturene 
kunne ikke verifiseres fordi den offentlige nøkkelen ikke er 
tilgjengelig: NO_PUBKEY EFDC8610341D9410
W: Klarte ikke å skaffe 
[http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  De følgende 
signaturene kunne ikke verifiseres fordi den offentlige nøkkelen ikke er
 tilgjengelig: NO_PUBKEY EFDC8610341D9410
W: Noen indeksfiler ble ikke lastet ned. De har enten blitt ignorert eller erstattet med gamle indeksfiler.

W: An error occurred during signature verification. Package storage is not updated, and previous index files are now being used. GPG Error Message: [http://repository.spotify.com](http://repository.spotify.com) Stack InRelease: The following signatures could not be verified because the public key is not available: NO_PUBKEY EFDC8610341D9410
W: Failed to obtain [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease) The following signatures could not be verified because the public key is unavailable: NO_PUBKEY EFDC8610341D9410
W: Some index files were not downloaded. They have either been ignored or replaced with old index files.

---

### Post by photonxp on 2017-11-22
Change 
    > sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
To
    > sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EFDC8610341D9410

Then 
sudo apt-get update

If that does not work, try

  > apt-get clean            # Remove cached packages
cd /var/lib/apt
mv lists lists.old       # Backup mirror info
mkdir -p lists/partial   # Recreate directory structure
apt-get clean
apt-get update           # Fetch mirror info
[https://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](https://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

---

### Post by aleddilwynfisher on 2017-11-22
I've tried the very popular and frequently used solutions offered here - [https://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot](https://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot) - before, without success. '

This is what happened when I tried this time: 

```
aled@aled-Inspiron-15-3552:~$ dpkg -l linux-{image,headers}-"[0-9]*" | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e '[0-9]' | xargs sudo apt-get -y purge
[sudo] passord for aled: 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold        
Leser tilstandsinformasjon ... Ferdig 
Du vil kanskje utføre «apt-get -f install» for å rette på disse:
Følgende pakker har uinnfridde avhengighetsforhold:
 linux-image-extra-4.4.0-75-generic : Avhenger av: linux-image-4.4.0-75-generic men skal ikke installeres
 linux-image-extra-4.4.0-77-generic : Avhenger av: linux-image-4.4.0-77-generic men skal ikke installeres
 linux-image-extra-4.4.0-78-generic : Avhenger av: linux-image-4.4.0-78-generic men skal ikke installeres
 linux-image-extra-4.4.0-79-generic : Avhenger av: linux-image-4.4.0-79-generic men skal ikke installeres
 linux-image-extra-4.4.0-81-generic : Avhenger av: linux-image-4.4.0-81-generic men skal ikke installeres
 linux-image-extra-4.4.0-83-generic : Avhenger av: linux-image-4.4.0-83-generic men skal ikke installeres
 linux-image-extra-4.4.0-93-generic : Avhenger av: linux-image-4.4.0-93-generic men skal ikke installeres
 linux-image-extra-4.4.0-97-generic : Avhenger av: linux-image-4.4.0-97-generic men skal ikke installeres
 linux-image-extra-4.4.0-98-generic : Avhenger av: linux-image-4.4.0-98-generic men skal ikke installeres
 linux-image-generic : Avhenger av: linux-image-4.4.0-98-generic men skal ikke installeres
E: Uinnfridde avhengighetsforhold. Prøv «apt-get -f install» uten pakker (eller angi en løsning).

```

TRANSLATIONS: 
Avhenger av = Depends on 
Men skal ikke installeres = But will/shall not be installed 
Uinnfridde avhengighetsforhold = Unresolved dependencies 
Prøv «apt-get -f install» uten pakker (eller angi en løsning) = Try "apt-get -f install" without packages (or set a solution)

I then tried "apt-get -f install" as suggested, and this was what I got: 

```
aled@aled-Inspiron-15-3552:~$ apt-get -f install
E: Klarte ikke åpne låsefila /var/lib/dpkg/lock - open (13: Ikke tilgang)
E: Klarte ikke låse den administrative mappen (/var/lib/dpkg/). Er du root?

```

TRANSLATIONS: 
Klarte ikke åpne = Couldn't manage to open 
Klarte ikke låsen den administrative mappen = Couldn't manage to load the admistrative folder 
Er du root? = Are you root?

---

### Post by aleddilwynfisher on 2017-11-22
> **photonxp said:**
> Change 
    
To
    

Then 
sudo apt-get update

If that does not work, try

  
[https://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](https://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

DISASTER!

I tried the first bit regarding keys and did sudo apt-get update, and there were no error messages anymore. So I rebooted it to check if the Broken Counter Error icon disappeared. 

But now my laptop won't boot up at all!

I get a black screen with white writing that says:

> GNU GRUB versjon 2.02 beta 2-36ubuntu3.11

Then I have three choices: Ubuntu, Advanced choices for Ubuntu, and two kinds of memory test.

Under ADvanced Choices, there are lists of all the different versions of Ubuntu available, with Upstart and Recovery Mode options. 

All of these lead to the same thing - a page full of code ended with:

> Kernel offset: disalbed 
End Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

What the hell do I do? I'm writing a PhD and I need my laptop to work - why is this happening and can it be fixed?

---

### Post by aleddilwynfisher on 2017-11-22
Found this - [https://askubuntu.com/questions/898449/kernel-panic-and-unable-to-boot-ubuntu-16-04-after-updating](https://askubuntu.com/questions/898449/kernel-panic-and-unable-to-boot-ubuntu-16-04-after-updating) - but I can't open a text only terminal, how do I do this?

---

### Post by photonxp on 2017-11-22
- hold down shift while booting so the grub menu shows up
- boot using another kernel (Try 4.4.0-89-generic with the first guess)

Or try Try 4.4.0-89-generic in "**Advanced options for Ubuntu**"

---

### Post by deadflowr on 2017-11-24
> why is this happening and can it be fixed?
You tried rebooting before finishing fixing broken packages,
as to why it now boots to all broken kernels? I'm not sure, that seems odd.
Please double check that they are all broken.

If they are all broken then can it be fixed? Yes.

If you have your Ubuntu installation disk/usb stick still, then fixing it is possible.

But since your system is an lvm setup (and maybe a full disk encrypted system at that) it's a bit more complicated that a usual chroot.
**(a chroot will allow you to run from the Ubuntu installation's live session utility, yet enter into your main installed system to make changes and fixes)

Two important things to know is if you
1) can get a network connection on the live session that you can start from the Ubuntu installation disk/usb stick
2) if this is a regular lvm system or an lvm + encryption setup.
(a non-encrypted lvm setup is a smidge easier to deal with than an encrypted lvm setup)

To tell which it is is simple. When you normally boot into Ubuntu do you have to enter a passphrase
(not the password that it asks for later at the login screen that also shows your username, but a passphrase even before it shows the login screen)
That would mean an encrypted setup.
(Note it you remember the name it shows at the passphrase (like it says Enter passphrase on /dev/sda5_crypt) then the /dev/sd name will help make things even easier to setup if need be you have to run a chroot)

But lets hope you can get a functional kernel from the boot menu, before going down that long an tedious road.

---

