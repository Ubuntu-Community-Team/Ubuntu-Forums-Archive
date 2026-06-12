---
title: "Compiling Endeavour 2 File Manager from Source, Nasty Error (Help Deciphering?)"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by wkdude18 on 2008-08-04
After copying the endeavour-2.9.2.tar.bz2 or something like that from the Linux Format 108 DVD to my hard drive, I did ```
tar -xvjf end(whatever).bz2
cd endeavour-2.9.2
./configure Debian --disable="libxar"
make all/gmake all (gmake symlinked to make, same thing)
```

Compiling module mime_type_edit_dlg.o
mime_type_edit_dlg.c: In function ‘EDVMimeTypeEditDlgCommandsCListDragDataGetCB’:
mime_type_edit_dlg.c:669: warning: pointer targets in passing argument 4 of ‘gtk_selection_data_set’ differ in signedness
mime_type_edit_dlg.c: In function ‘CmdDlgCListDragDataGet’:
mime_type_edit_dlg.c:1256: warning: pointer targets in passing argument 4 of ‘gtk_selection_data_set’ differ in signedness
mime_type_edit_dlg.c:3146:1: warning: missing terminating " character
mime_type_edit_dlg.c: In function ‘CmdDlgNew’:
mime_type_edit_dlg.c:3146: error: missing terminating " character
mime_type_edit_dlg.c:3148: error: ‘multiple’ undeclared (first use in this function)
mime_type_edit_dlg.c:3148: error: (Each undeclared identifier is reported only once
mime_type_edit_dlg.c:3148: error: for each function it appears in.)
mime_type_edit_dlg.c:3148: error: expected ‘)’ before ‘arguments’
mime_type_edit_dlg.c:3148: error: stray ‘\’ in program
mime_type_edit_dlg.c:3354: error: expected ‘;’ before ‘}’ token
mime_type_edit_dlg.c:2806: warning: unused variable ‘parent6’
mime_type_edit_dlg.c:3354: warning: control reaches end of non-void function
gmake[1]: *** [mime_type_edit_dlg.o] Error 1
gmake: *** [all] Error 1

Sorry for making you look at that :) But, if this makes no sense to you, but you are good at compiling from source, not because you've never done it before, here is the contents of the INSTALL file in the endeavour-2.9.2 directory:

      E N D E A V O U R   M A R K   I I

             I N S T A L L A T I O N   I N S T R U C T I O N S


==============================
STEP 1: CONFIGURING THE SOURCE

	Run a terminal and "cd" to the same directory that this file is
	located in, then type:

	# ./configure --listall

	This will run the compiler test and print all available 
	platforms. Choose the most appropriate platform for your
	situation and add any additional arguments as needed.

	If the configure test failed after typing the above command then
	it may indicate that you may not be able to compile or run this
	program on your system, please contact the authors or post a
	message on the Endeavour 2 mailing list and ask for help in this
	situation. Read the file AUTHORS for a list of addresses.

	For more information on enabling/disabling and overriding
	configuration values, type:

	# ./configure --help

	To configure the source, type ./configure and then the name
	of the platform followed by any additional arguments, for
	example:

	# ./configure Linux

	or

	# ./configure Linux --prefix=/usr -v --enable="arch-i586"

	For local installations (installing the program to a
	subdirectory in your home directory) you need to specify a
	--prefix value that is the full path to your home directory or
	the full path to a subdirectory within your home directory,
	for example:

	# ./configure Linux --prefix=/home/myname


	If you intend to compile this program with text displayed in a
	language other than English then you need to edit the file:

	$TOPLEVEL/endeavour2/config.h

	Near the top of the file you will find the lines:

	#define PROG_LANGUAGE*

	You will need to comment out all of them except for the language
	that you want. Then save this file and continue to the next
	step.


======================================
STEP 2: BUILDING/COMPILING THE PROGRAM

	If there were no problems configuring the source then type:

	# gmake all

	or

	# make all

	This will start the compiling process.

	If you do not have "gmake" then use "make", otherwise try
	"gmake" first.

	If you encountered errors orproblems then you should report them
	to the authors. Read the AUTHORS file for a list of addresses.


====================
STEP 3: INSTALLATION

	For global installations (default prefix is /usr), type "su" to
	switch to the root user and then type:

	# gmake install

	For local installations, type:

	# gmake install

	Remember that local and global installations were determined
	by the --prefix value that you gave when configuring the source.

	Installation locations are as follows ($PREFIX is replaced with
	the value of --prefix that you provided when configuring the
	source):

	$PREFIX/bin/endeavour2
	$PREFIX/bin/endeavour2-config

	$PREFIX/lib/libendeavour2.so
	$PREFIX/lib/endeavour2/

	$PREFIX/man/man1/endeavour2-config.1.bz2
	$PREFIX/man/man1/endeavour2.1.bz2

	$PREFIX/share/endeavour2/

	$PREFIX/share/icons/endeavour2.xpm
	$PREFIX/share/icons/endeavour2_archiver.xpm
	$PREFIX/share/icons/endeavour2_image_browser.xpm
	$PREFIX/share/icons/endeavour2_trash.xpm
	$PREFIX/share/icons/endeavour2_trash_empty.xpm


	Note that there are no MIME Types list files included in this
	package, to obtain and install MIME Types list files, go to:

	[http://www.battlefieldlinux.com/wolfpack/Endeavour2/contrib](http://www.battlefieldlinux.com/wolfpack/Endeavour2/contrib)


	All Endeavour 2 utility programs and third party programs
	for Endeavour 2 are installed in:

	$PREFIX/lib/endeavour2/bin/


===============
STEP 4: RUNNING

	To run this program, type:

	# endeavour2 &

	When you run this program for the first time, directories for
	all local data files will be created in your home directory.

        For additional command line options, type:

        # endeavour2 --help

	or

	# man endeavour2


	There are additional Endeavour 2 related utility programs
	installed in /usr/lib/endeavour2/bin/

                                                      =================
                                                      ENDEAVOUR MARK II

---

### Post by chiefchimp on 2008-08-04
> **wkdude18 said:**
> After copying the endeavour-2.9.2.tar.bz2 or something like that from the Linux Format 108 DVD to my hard drive, I did ```
tar -xvjf end(whatever).bz2
cd endeavour-2.9.2
./configure Debian --disable="libxar"
make all/gmake all (gmake symlinked to make, same thing)
```

Compiling module mime_type_edit_dlg.o
mime_type_edit_dlg.c: In function ‘EDVMimeTypeEditDlgCommandsCListDragDataGetCB’:
mime_type_edit_dlg.c:669: warning: pointer targets in passing argument 4 of ‘gtk_selection_data_set’ differ in signedness
mime_type_edit_dlg.c: In function ‘CmdDlgCListDragDataGet’:
mime_type_edit_dlg.c:1256: warning: pointer targets in passing argument 4 of ‘gtk_selection_data_set’ differ in signedness

the source code is mixing references to variables as both unsigned and signed which GCC 4 doesn't like, sloppy but usually ok 
> **wkdude18 said:**
> mime_type_edit_dlg.c:3146:1: warning: missing terminating " character
mime_type_edit_dlg.c: In function ‘CmdDlgNew’:
mime_type_edit_dlg.c:3146: error: missing terminating " character
mime_type_edit_dlg.c:3148: error: ‘multiple’ undeclared (first use in this function)
the code before line 3146 of mime_type_edit_dlg.c contains an unterminated  text string (probably the string continues on the next line).
anything the compiler sees/reports after this point is "garbage"

---

