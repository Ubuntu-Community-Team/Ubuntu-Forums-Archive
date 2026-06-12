---
title: "Custom Kernel and Ubuntu Module Rebuild Process"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by tgilber1 on 2008-09-06
After much trouble and consternation, I believe that I have found a way to recompile both a custom Ubuntu kernel and its third-party modules using the AUTOBUILD and debian/rules.  The reason I went through the hassle of figuring this out was due to the Ubuntu updates continuously wanting to overwrite my patches.  Hence, I look into different ways, including make-kpkg and debian/rules.  The make-kpkg provides a rich set of environment varaible such as DEBIAN_REVISION.  Unfortunately, I have not been able to successfully compile the ubuntu third-party modules.  Additionally, the make-kpkg environment variable do not carry over to the AUTOBUILD debian/rules.  Fortunately, after many days and weeks of struggling to achieve success, I figured out the process to use the debian rules to rebuild both the kernel and modules in Ubuntu.  Below are the steps.  Hopefully, these instructions work for you.

1.  Download latest git kernel version  
	a.  Download latest Ubuntu git kernel with git clone git://kernel.ubuntu.com/ubuntu/<ubuntu-git-tree>.git <my_kernel_directory>
		#e.g., Open vi terminal and type "git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git myubuntu"

		Note:  If git address fails, check Google or Ubuntu for updated location(s)
	b.  cd <git-kernel-directory> #e.g., cd myubuntu
	c.  git pull # to get latest patch.  Should already be the latest, should be already set
	d.  git tag - to see all versions and revisions.  Decide which kernel version and revision to use in next step
	e.  git checkout -b new <kernel version-abi-revision> #e.g., git checkout -b new Ubuntu-2.6.24-21.42
	f.  git branch # should show branch new with an asterisk beside it #e.g., *new
	g.  git show # should show version that is checked out, which should reflect the kernel the directory is pointed to

	
2. Create custom directory using name that will append to kernel-version.  The name of the new directory will be appended to the kernel version after a succesful recompile
	a.  cd <git-kernel-directory>/debian/binary-custom.d #e.g., cd /home/test/myubuntu/debian/binary-custom
	b.  mkdir <custom> #e.g., mkdir mycustom

3.  Create at least three files and one directory in the new custom directory
	a.  cd <custom> #e.g., cd mycustom
	b.  create a config.<arch> file for each architecture that requires rebuilding
		cp /boot/config-<kernel-version>.arch #e.g., cp /boot/config-2.6.24-21-generic config.amd64
		cp /boot/config-<kernel-version>.arch #e.g., cp /boot/config-2.6.24-21-generic config.i386
	c.  create a vars file to pass custom variable for custom kernel
		cp ../rt/vars ./vars
	d.  edit vars file and remove non-pertinent information, i.e., target info line
	e.  create patchset directory
		mkdir patchset #copy patch files over to this directory, if any
	f.  create rules file
		touch rules #leave empty if nothing to be done

4.  Edit files, Makefile, 0-common-vars.mk and all pertinent <arch>.mk files, add new binary.d/custom directory name to each file for custom flavours.  Hint:  append each line you see other customer flavours (xen, rt, etc.) populated.
	a.  vi 	<git-kernel-directory>/Makefile #remove the value on the EXTRAVERSION, in order to recompile will get the correct release number 2.6.24-[21]
	b.  vi <git-kernel-directory>debian/rules.d/0-common-vars.mk #e.g., all_custom_flavours = rt xen custom
	c.  vi <git-kernel-directory>debian/rules.d/<arch>.mk #e.g.,  /home/test/myubuntu/debian/rules.d/amd64.mk #e.g., custom_flavours= rt xen custom

5.  Remove control.stub file and to generate new debian/control, which includes new custom kernel
	a.  cd <git-kernel-directory>
	b.  rm debian/control.stub #remove control.stub, otherwise, following command will not create new one
	c.  ./debian/rules debian/control.stub #creates new control.stub and control files
	d.  view new control to verify that custom kernel is in debian/control file

6.  Build custom kernel
	a.  AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-<custom> #e.g., AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-mycustom
	b.  After successful compilation, both the image and headers files will be copied up one directory from the original <git-kernel-directory>



Add third-party modules, i.e., the sub-directory of modules directory called ubuntu (e.g., /lib/modules/2.6.24-21-custom/ubuntu)

1.   Download latest git ubuntu-lum version  
	a.  Download latest Ubuntu git kernel with git clone git-clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy-lum.git <my_ubuntu_modules_directory>
		#e.g., Open vi terminal and type "git clone git://kernel.ubuntu.com/ubuntu/ubuntu/ubuntu-hardy-lum.git myubuntu-modules"

		Note:  If git address fails, check Google or Ubuntu for updated location(s)
	b.  cd <git-kernel-directory> #e.g., cd myubuntu-modules
	c.  git pull # to get latest patch.  Should already be the latest, should be already set
	d.  git tag - to see all versions and revisions.  Select kernel version and revision to use; proceed to next step
	e.  git checkout -b new <kernel version-abi-revision> #e.g., git checkout -b new Ubuntu-2.6.24-21.32
	f.  git branch # should show branch new with an asterisk beside it #e.g., *new
	g.  git show # should show version that is checkout, which should reflect the kernel the directory is pointed to


2.  Copy vars.rt file to vars.<custom> 
	a.  cp myubuntu-modules/debian/control.d/vars.rt myubuntu-modules/debian/control.d/vars.mycustom.  

	Note: Custom modules name must match the custom kernel name

3.  Edit vars.<custom> #e.g., vi myubuntu-modules/debian/control.d/vars.mycustom 
	a.  Below is an example what I put in this file.  I removed the line that begins with provides to avoid compile error.  The # sign is for 		    this explanation, only.  Hence, it does not have to be populated in the file.

	desc="x86/x86_64" #description
	arch="i386 amd64" #architecture
	section_image="universe/base" #what software section this deb belongs to

4.  Edit <arch>.mk files in the rules.d directory and add to the flavours line, next to the other custom flavours, e.g., xen rt mycustom
	a.  vi myubuntu-modules/debian/rule.d/amd64.mk

5.  Remove control.stub file and to generate new debian/control, which includes new custom kernel
	a.  cd <git-ubuntu-modules-directory> #e.g., cd myubuntu-module
	b.  rm debian/control.stub #remove control.stub, otherwise, following command will not create new one
	c.  ./debian/rules debian/control.stub #creates new control.stub and control files
	d.  view new control to verify that custom kernel is in debian/control file

6.  fakeroot debian/rules binary-arch arch=amd64 flavours="mycustom"

	arch = platform such i386, amd64, etc.
	flavours = custom builds such xen, rt, or <custom>


7.  The deb filenames will consist of two parts, the first of the new filename is the version info with the appended custom name.  The second part points to the the version and revision that the kernel was built against.

	linux-headers-2.6.24-21-time_2.6.24-21.42_amd64.deb
	linux-headers-lum-2.6.24-21-time_2.6.24-21.32_amd64.deb
	linux-image-2.6.24-21-time_2.6.24-21.42_amd64.deb
	linux-ubuntu-modules-2.6.24-21-time_2.6.24-21.32_amd64.deb

8.  Lastly, step six will generate udeb error messages, but it does not fail the kernel from recompiling and generating all the deb files.  To eliminate the udeb error messages, Edit 0-common-vars.mk file and set the disable_d_i line to true or edit the kernel-version and kernel-version.in located in the <Ubuntu-modules>/debian/d-i & <Ubuntu-modules>/debian/d-i-<arch> and replace the arch line with the new custom kernel filename.

---

### Post by cheoppy on 2008-10-13
Hi!

What kind of patches did you apply to the Ubuntu kernel?
I'm trying to make a similar process to integrate TuxOnIce nicely into my Ubuntu kernels and I might have some questions.

---

