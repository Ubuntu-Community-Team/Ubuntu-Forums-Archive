---
title: "While trying to fix ALSA, broke all updates?"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by AbeFM on 2012-08-12
So, I've had this weird sound issue forever, so I ran through the sound fixing script, which is supposed to make it possible to post logs. 
(from [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) )
well, once I did, my issues went away - so I guess there's no luck in figuring out what happened to help others in the future.

The issue is now every update or install fails!
More completely described over at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034287](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034287)
basically, every install exits with:
```
  Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010.
```
but for all of the following:
while processing:
 linux-image-3.2.0-23-generic
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-25-generic
 linux-image-3.2.0-26-generic
 linux-image-3.2.0-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Looking at thread [http://ubuntuforums.org/showthread.php?p=12127583](http://ubuntuforums.org/showthread.php?p=12127583)

it looks like there might be a way out of this - but I don't think watershed is my issue. Can someone point me in the right direction here?

(FYI, the output of sudo apt-get -qq install linux-image-3.2.0-27-generic > aptlog.txt is:
```
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-24.39 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-24.39 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-25-generic (3.2.0-25.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-25.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-25.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-25-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-26.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-26.41 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-27.43 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-27.43 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-25-generic
 linux-image-3.2.0-26-generic
 linux-image-3.2.0-27-generic
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
```

the only thing that jumps out at me is it's choosing not to update links since it's an update - which I think it should.

My machine's quite close to working well for once, if I could only install/update I think I'd be "done". :-)

---

### Post by AbeFM on 2012-08-28
I really hope this helps!

Some software package which used to be stable now isn't and my computer crashes occasionally when running it. There are updates which I can't install and in short my computer is becoming unusable.

Since, as shown above, it's always while configuring GRUB it throws errors - specifically zz-update-grub - I thought I would "reinstall" everything with "grub" in the title under synaptic.

First few lines of that process:

```
Preconfiguring packages ...
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libass4' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.

```

Looks like libass4 is truncated. Is there some way I can regenerate that from scratch? Like my earlier suggestion of forcing links to update, from error:
> Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-24.39 was configured last, according to dpkg)

makes me think I just need to get something, somewhere to reinstall.

PLEASE PLEASE PLEASE tell me which rock to look under and I'll do it. I'm happy to dig as long as it takes if only someone who knows what to even try can point me in the right direction.

Thank you.

---

### Post by AbeFM on 2012-08-28
as an aside, I'm seeing  images up to 3.2.0.40, it's only seemingly having errors with numbers 23-29. Don't know if this helps.

```
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-25-generic
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-image-3.2.0-23-generic
 linux-generic
 linux-image-3.2.0-27-generic

```

So, that makes me think I could remove and reinstall libass4 - it's merely for subtitles, only if I remove it, it will remove VLC, homerun, and pithos, which I use daily, and if I uninstall pithos and can't reinstall it my computer will go from irritating to entirely pointless.

I did try a reinstall, which of course didn't work. I'd like someone to tell me there's a snowball's chance of this thing working before I do it.

---

### Post by Zorael on 2012-09-03
What happens if you run update-grub manually? Is there anything of interest output to the terminal?

As for libass4, that sounds like a packaging issue. If it isn't already fixed in the repos, you can locally add the newline yourself, yes.

Hmm;
```
#!/bin/sh
# this adds missing ending newlines to package list files

LISTDIR=/var/lib/dpkg/info

# create a temporary directory to save backups to
BACKUPDIR=$(mktemp -d /tmp/listbackups-XXXXXX) || exit 1

# go!
for listfile in $LISTDIR/*.list; do
	# print some progress dots as user feedback
	printf "."

	# if the last line of the list file contains a newline,
	# just nod in approval and proceed to the next one
	[ $(tail -n1 $listfile | wc -l) -gt 0 ] && continue

	# non-purged but removed packages may leave behind empty list files,
	# which would pass the above check (there are no newlines at all).
	# aptitude purge ~c fixes those, fwiw
	[ $(wc -c < $listfile) -eq 0 ] && continue

	##########################################################################

	# if we're here we know the file needs fixing

	filename=${listfile##*/}
	printf "\nmissing newline in %s; backing up to %s/ before appending\n" \
		"$filename" $BACKUPDIR

	# we do a dry run by default unless explicitly forced
	if [ ! "$1" = "please" ]; then
		printf "actually no, you didn't ask very nicely! :(\n"
		printf "say '%s please' next time\n" "${0##*/}"
		# to the next file!
		continue
	fi

	# backing up first is always a good idea
	cp -v $listfile $BACKUPDIR/$filename || exit 1

	# 'tee -a' appends. exit on errors as that likely means sudo auth failure
	printf "\n" | sudo tee -a $listfile 1>/dev/null || exit 1
done

printf "\n\ndone\n"

# try to remove the backup directory; this will only work if it's empty.
# if it has contents (saved backups) nothing happens. rmdir just works like that.
rmdir --ignore-fail-on-non-empty $BACKUPDIR

exit 0
```

---

### Post by AbeFM on 2012-09-03
Huh, so, I'm supposed to save that as a file, run it as a script? Seems to make sense, though it looks like it goes after ALL .list files which are missing newlines.

I **had** tried to edit the file manually, but it didn't show up in proper encoding. Very odd.

Anyway, as seen in other threads, I was able to completely remove libass4 (along with Pithos and HomeRunGUI) by removing ALL files in var/bin/dpkg/info assosiated with those packages.

And, re installed pithos and did some cleanups, and got system up to date. I feel it wasn't the right way to do it, but it did work.

I still think it might not hurt to clean up grub.

Right now it still hangs up on linux-generic-3.2.023 - but no other versions. Of course, THIS file won't respond as the rest, it's harder to remove.

I'm guessing I'll have to post more information, is there anywhere you'd like me to start?

edit: I actually moved all the files, so I still have them

---

### Post by Zorael on 2012-09-04
Yes, the script would go through them all, just to be thorough if you have any other weird breakages. Deleting the files outright would also sort-of-work, as you trick dpkg into losing track of the package entirely.

You mention that it "hangs" at -23; do you mean that the updating stops or that it actually never completes?

Again, could you post that '**sudo update-grub**' terminal output? It's obviously exiting with errors.

If possible I'd also like to see the output of apt and dpkg trying to configure and fix those packages;
```
$ sudo apt-get install -f
$ sudo dpkg --configure -a
```

---

### Post by AbeFM on 2012-09-04
```
root@HBO:/home/abe# update-grub
Generating grub.cfg ...
root@HBO:/home/abe#
```

Nothing too cool there, though I wonder if things changed since all the other changes. I haven't seen as many complaints during updates. 

I ran these:
```
mv /var/lib/dpkg/info/linux-image-3.2.0-2*.* /var/lib/dpkg/info/temp
apt-get remove linux-image-3.2.0-2*.*

```

and now as I mentioned, only the 23 file complains anymore. 

I'll run a system update, which now mostly works, and get you the output, the last 1/3 or so is all errors with Grub and .023 generic:

entire output:
```

installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 224859 files and directories currently installed.)
Preparing to replace icedtea-6-jre-cacao 6b24-1.11.3-1ubuntu0.12.04.1 (using .../icedtea-6-jre-cacao_6b24-1.11.4-1ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement icedtea-6-jre-cacao ...
Preparing to replace openjdk-6-jre-lib 6b24-1.11.3-1ubuntu0.12.04.1 (using .../openjdk-6-jre-lib_6b24-1.11.4-1ubuntu0.12.04.1_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
Preparing to replace icedtea-6-jre-jamvm 6b24-1.11.3-1ubuntu0.12.04.1 (using .../icedtea-6-jre-jamvm_6b24-1.11.4-1ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement icedtea-6-jre-jamvm ...
Preparing to replace openjdk-6-jre-headless 6b24-1.11.3-1ubuntu0.12.04.1 (using .../openjdk-6-jre-headless_6b24-1.11.4-1ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement openjdk-6-jre-headless ...
Preparing to replace handbrake-gtk 4929svnppa1~precise1 (using .../handbrake-gtk_4930svnppa1~precise1_amd64.deb) ...
Unpacking replacement handbrake-gtk ...
Preparing to replace openjdk-6-jre 6b24-1.11.3-1ubuntu0.12.04.1 (using .../openjdk-6-jre_6b24-1.11.4-1ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement openjdk-6-jre ...
Preparing to replace openjdk-6-jdk 6b24-1.11.3-1ubuntu0.12.04.1 (using .../openjdk-6-jdk_6b24-1.11.4-1ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement openjdk-6-jdk ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up handbrake-gtk (4930svnppa1~precise1) ...
Setting up openjdk-6-jre-lib (6b24-1.11.4-1ubuntu0.12.04.1) ...
Setting up openjdk-6-jre-headless (6b24-1.11.4-1ubuntu0.12.04.1) ...
update-binfmts: warning: current package is openjdk-6, but binary format already installed by openjdk-7
Setting up icedtea-6-jre-cacao (6b24-1.11.4-1ubuntu0.12.04.1) ...
Setting up icedtea-6-jre-jamvm (6b24-1.11.4-1ubuntu0.12.04.1) ...
Setting up openjdk-6-jre (6b24-1.11.4-1ubuntu0.12.04.1) ...
Setting up openjdk-6-jdk (6b24-1.11.4-1ubuntu0.12.04.1) ...
Errors were encountered while processing:
 linux-image-3.2.0-23-generic
Error in function: 
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2


```

Interestingly, I also see issues with 3.2.0-23.36? Not even sure what the difference is. What I find odd, when I uninstalled pithos, and it came back, it kept all my settings, so the "completely remove" didn't really work, likely since I'd moved all those files before removing.

---

### Post by AbeFM on 2012-09-05
So after continued issues, I thought I'd look at this line 1010 in linux-image-3.2.0-23-generic.postinst, and ran the command it's trying to run:


```
root@HBO:/home/abe# run-parts --verbose --exit-on-error --arg=3.2.0-23-generic /etc/kernel/postinst.d
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
root@HBO:/home/abe# 

```

Well, if it dies on zz-update-grub, I run that:
```
root@HBO:/home/abe# /etc/kernel/postinst.d/zz-update-grub
Generating grub.cfg ...
root@HBO:/home/abe# 
```
As the other attempts at updating grub, it works fine. 

So what's the issue? No idea. relevant section of postinst:```
if (-d "/etc/kernel/postinst.d") {
  print STDERR "Examining /etc/kernel/postinst.d.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
```

Perhaps it's "exit-on-error" that's killing me? 

```
root@HBO:/home/abe# run-parts --verbose --arg=3.2.0-23-generic /etc/kernel/postinst.d
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
root@HBO:/home/abe# 

```



Looking at zz-update-grub:
```
#! /bin/sh
set -e

which update-grub >/dev/null 2>&1 || exit 0

set -- $DEB_MAINT_PARAMS
mode="${1#\'}"
mode="${mode%\'}"
case $0:$mode in
    # Only run on postinst configure and postrm remove, to avoid wasting
    # time by calling update-grub multiple times on upgrade and removal.
    # Also run if we have no DEB_MAINT_PARAMS, in order to work with old
    # kernel packages.
    */postinst.d/*:|*/postinst.d/*:configure|*/postrm.d/*:|*/postrm.d/*:remove)
	exec update-grub
	;;
esac

exit 0
```
There must be something I'm not seeing (esac?) since I don't see it saying to return with code 1 anywhere!



Huh. So I commented out the entire offending if statement in that postinst file, and everything seems to run smooth as silk. It seems a silly fix, but perhaps am I better off that way? Won't G
rub get updated by the 20 other things (i.e. version 3.2.0.NOT23) which do it?

I guess post and let me know what you think. A very unsatisfying fix, i.e. I don't think it'll lead to discovering a bug and fixing linux as a whole... But it might get me running.

---

### Post by Zorael on 2012-09-06
(**esac** is just the ending of **case**, just like **fi** is for **if**. :3)

As for exiting with errors, both **update-grub** and **grub-mkconfig** set the sh builtin option '**set -e**';
```
-e errexit  If not interactive, exit immediately if any untested command fails.
            The exit status of a command is considered to be explicitly tested if
            the command is used to control an if, elif, while, or until; or if the
            command is the left hand operand of an “&&” or “||” operator.
```

So if any untested command *anywhere* in either of those scripts "fail", the entire thing stops. Using it makes it easier to stop scripts from continuing when it shouldn't, without having to check every single command and catch errors manually. *Usually* you get a descriptive error message though.

To illustrate;
```
#!/bin/sh
**set -e**

**chmod -f 000 /filethatdoesnotexist**
echo "The script will never get here as the above command fails (exits with >0; file not found)"
```

Try changing **set -e** in /usr/sbin/grub-mkconfig to **set -e_x_**. It will be a bit spammy as it prints out every line as it executes them, but you'll hopefully see where it stops.

---

### Post by AbeFM on 2012-09-10
Computer decided not to boot anymore, though everything was going strong for a few days and a few reboots.

So a quick install - which took quite a bit less time, likely by a factor of 8-10, than I've spent trying to fix all this.

New set up, with 12.10.... Same sound issue, networking gui is messed up (can't share stuff), but most of my other work arounds went super quick.

I do like that you can change mount options (though sorely lacking check boxes, it still makes more sense) in Disk Manager, but not liking that spinning down drives isn't handled anywhere like power management or disk mounter, and that the raid has to be handled as a series of separate disks.

All in all, it's amazing to have a computer that, so far, seems to work overall.

Thanks so much for trying to help. I'd loved to have tracked it down to turn in a good bug report, but I can't get anyone to listen anyway so there seems little point to figuring stuff out (like, why must I put "remix LFE" into a text file when it KNOWS I have a 5.1?)

---

