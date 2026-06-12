---
title: "make test failed"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by pascale on 2008-03-17
hi,
i am new to ubuntu and i m really struggling to compile/install a source code. it is a bioinfo software ([http://meme.sdsc.edu/meme/meme-download.html](http://meme.sdsc.edu/meme/meme-download.html)). "./configure" and "make" ran smoothly. but when i tried "make test", this is the error message i get:

[COLOR="Green"]cd scripts; make check
make[1]: Entering directory `/home/mathonet/Desktop/meme/meme_3.5.7/scripts'
make  check-TESTS
make[2]: Entering directory `/home/mathonet/Desktop/meme/meme_3.5.7/scripts'

              Meme test for 
    ---------------------------------
      Dataset       Model     result 
    ---------------------------------
    crp0            oops       OK
    crp0            zoops      OK
    crp0            tcm        OK

              Mast test for 
    ---------------------------------
      Dataset       Model     result 
    ---------------------------------
Can't exec /bin/csh at /home/mathonet/Desktop/meme/meme_3.5.7/scripts/../scripts/make_logodds line 1.
basename: missing operand
Try `basename --help' for more information.
The motif alphabet -MF appears to be a protein alphabet
but is missing the required letter `A'.
    crp0            oops       FAIL
Can't exec /bin/csh at /home/mathonet/Desktop/meme/meme_3.5.7/scripts/../scripts/make_logodds line 1.
basename: missing operand
Try `basename --help' for more information.
The motif alphabet -MF appears to be a protein alphabet
but is missing the required letter `A'.
    crp0            zoops      FAIL
Can't exec /bin/csh at /home/mathonet/Desktop/meme/meme_3.5.7/scripts/../scripts/make_logodds line 1.
basename: missing operand
Try `basename --help' for more information.
The motif alphabet -MF appears to be a protein alphabet
but is missing the required letter `A'.
    crp0            tcm        FAIL

FAIL: runcheck
===================
1 of 1 tests failed
===================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/home/mathonet/Desktop/meme/meme_3.5.7/scripts'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/home/mathonet/Desktop/meme/meme_3.5.7/scripts'
make: *** [test] Error 2[/COLOR]

and when i try the basename --help:

[COLOR="Green"]Usage: basename NAME [SUFFIX]
  or:  basename OPTION
Print NAME with any leading directory components removed.
If specified, also remove a trailing SUFFIX.

      --help     display this help and exit
      --version  output version information and exit

Examples:
  basename /usr/bin/sort       Output "sort".
  basename include/stdio.h .h  Output "stdio".

Report bugs to <bug-coreutils@gnu.org>.[/COLOR]

does anyone have an idea how to fix that?
thanks in advance.....

---

### Post by dstew on 2008-03-17
It looks like there is an error in the make_logodds script. Take a look at it and see. The linux command **basename** takes a path as an argument and returns the last part ot the path, as the examples show. Probably there is nothing wrong with the basename program, but with the script. Maybe there is a typo or funny character in the basename argument. Maybe the script is trying to feed basename an argument, like an environmental variable, that hasn't been defined, or maybe one that is defined differently in whatever linux system the script writer used to create the script.

---

### Post by pascale on 2008-03-18
hi dstew,
thanks for your reply. i have copied the script below. to be honest, i have no idea where the basename is supposed to be. i am completely novice in the field.... is it possible that the problem is coming from the fact that ubuntu is coming with dash instead of csh?
thanks again for your help

#!/bin/csh -f
#
## $Id: make_logodds.txt 587 2006-03-08 20:50:14Z nadya $
## $Log$
## Revision 1.3  2006/03/08 20:50:11  nadya
## merge chamges from v3_5_2 branch
##
## Revision 1.2.4.1  2006/01/31 20:50:43  nadya
## add '-f' flag to prevent sourcing init files
## was causing problem on cygwin
##
## Revision 1.2  2005/10/04 17:46:58  nadya
## use full path for "rm". Some systems set rm alias that ask for confirmation.
##
## Revision 1.1.1.1  2005/07/28 23:55:47  nadya
## Importing from meme-3.0.14, and adding configure/make
##
#

set perl = @WHICHPERL@
# tlb 3-28-00; add support of new GCG profile format; change count to 100000
if ($#argv < 2) then
  cat << "USAGE"
 USAGE:
	make_logodds <mfile> <logodds> [-c count] [-D dir]

		<mfile>		name of file containing motifs
		<logodds>	name of file for output
		[-c count]	output only the first -c motifs

	Read the log-odds matrices from a meme, blockmaker or GCG profile file.
	Profile files may be concatenated together.

	The file output has format:
		[<w> <alength> <evalue> [<pair>]\n
                <column 1 of motif log-odds matrix>
                <column 2 of motif log-odds matrix>
                ...
                <column w of motif log-odds matrix>
                ]+

	Prints:
		<alphabet> [<sequence dataset>]

"USAGE"
  exit 1
endif

# get input
set mfile = $1
shift
set logodds = $1
shift
echo -n "" >! $logodds
if ($logodds != "/dev/null") then 
  chmod 744 $logodds
endif
set count = 100000
while ("$1" != "")
  switch ($1)
  case -c:
    	shift
    	set count = $1
	breaksw
  endsw
  shift
end

# make awk script to get stuff from mfile
set awk = make_logodds.awk.$$.tmp
onintr cleanup

cat << "END" > $awk
  NR == 1 {			# don't use BEGIN due to bug in awk
    count=count + 0;		# make numeric
    width=0; 			# default value
    alpha = "";			# default value
    evalue=0; 			# default value
    pair=0;			# default value
    old_alpha = "";
    dataset = "";		# default value
    nmatrices=0; 		# number of matrices read
  }
  $1 == "DATAFILE=" {dataset = $2;}
  $1 == "ALPHABET=" {alpha = $2;}
  $1 == "data:" {n = $3; N = $5;}
  $1 == "(best)" && $4 == "e_ll" { evalue = $9; }

  # meme format
  $1 == "log-odds" && $2 == "matrix:" {
    if (nmatrices++ >= count) next;	# skip this matrix
    # parse the log-odds matrix line
    for (i=3; i<=NF; i++) {
      if ($i == "alength=") {
        i++; alength = $i + 0;		# add 0 in case garbage
      } else if ($i == "w=") {
        i++; w = $i + 0;
      } else if ($i == "E=") {
        i++; evalue = $i + 0;
      } else if ($i == "pair") {
        pair = 1;
      }
    } # parse header line

    # print the header line for the matrix
    print w, alength, evalue, pair > logodds

    # copy the matrix to the logodds file; allow for rows to be contain newlines
    tot = 0;				# total fields read
    while (tot < w * alength) {		# read lines until alength fields read
      if (!(getline)) {			# read next line; extra parens for some
					# versions of awk/gawk (eg, gnu)
	printf \
	  "End of file reached while reading score matrix %s.\n", nmatrices;
	status = 1; exit;
      }
      #print "tot = ", tot, "NF = ", NF;
      for (i=0; i<NF; i++) lo[tot++] = $(i+1);	# store fields in matrix
      if (tot > w * alength) {
	printf \
	  "Number of entries not correct for matrix %s.\n", nmatrices;
	status = 1; exit;
      }
    }
    k = 0;
    for (i=0; i<w; i++) {		# row of logodds matrix
      for (j=0; j<alength; j++) {	# column of logodds matrix
        printf "%s ", lo[k] > logodds;
        k++;
      }
      printf "\n" > logodds;
    }
  }

  # new profile format
  $1 == "Cons" && $(NF-1) == "Gap" {
    if (nmatrices++ >= count) next;     # skip this matrix
    alength = NF - 3;                   # length of alphabet
    # get the alphabet from the first line
    alpha = "";
    for (i=2; i<NF-1; i++) alpha = alpha $(i);
    # check that alphabet hasn't changed
    if (old_alpha != "" && alpha != old_alpha) {
      print "All profiles must use exactly the same alphabet."
      print "The first " nmatrices-1 " motif(s) use " old_alpha;
      print " but motif " nmatrices " uses " alpha ".";
      status = 1; exit;
    }
    old_alpha = alpha;					# save alphabet
    # read the matrix
    for (line = 0; getline && $1 != "*"; line++) {
      # skip comments and blank lines and "}"
      first = substr($1,1,1);
      if (first == "!" || first == "}" || NF == 0 ) {line--; continue;}	
      if (NF != alength+3) {
        printf \
	  "Alphabet length does not match number of scores in matrix %s.\n", \
          nmatrices;
	status = 1; exit;
      }
      matrix[line] = "";
      # save line skipping consensus letter
      for (i=0; i<alength; i++) matrix[line] = matrix[line] " " $(i+2);
    }
    w = line;		 		# width of motif
    # print the header line for the matrix
    print w, alength, evalue, pair > logodds
    # copy the matrix to the logodds file
    for (i=0; i<w; i++) { print matrix[i] > logodds }
  }

  # old profile format
  $1 == "Cons" && $NF == ".." {
    if (nmatrices++ >= count) next;	# skip this matrix
    alength = NF - 4;			# length of alphabet
    # get the alphabet from the first line
    alpha = "";
    for (i=0; i<alength; i++) alpha = alpha $(i+2);
    # check that alphabet hasn't changed
    if (old_alpha != "" && alpha != old_alpha) {
      print "All profiles must use exactly the same alphabet."
      print "The first " nmatrices-1 " motif(s) use " old_alpha;
      print " but motif " nmatrices " uses " alpha ".";
      status = 1; exit;
    }
    old_alpha = alpha;					# save alphabet
    # read the matrix
    for (line = 0; getline && $1 != "*"; line++) {
      # skip comments and blank lines
      if (substr($1,1,1) == "!" || NF == 0) {line--; continue;}	
      if (NF != alength+3) {
        printf \
	  "Alphabet length does not match number of scores in matrix %s.\n", \
          nmatrices;
	status = 1; exit;
      }
      matrix[line] = "";
      # save line skipping consensus letter
      for (i=0; i<alength; i++) matrix[line] = matrix[line] " " $(i+2);
    }
    w = line;		 		# width of motif
    # print the header line for the matrix
    print w, alength, evalue, pair > logodds
    # copy the matrix to the logodds file
    for (i=0; i<w; i++) { print matrix[i] > logodds }
  }
   
  END {
    if (status) exit status;
    if (alpha == "") {
      print "Could not find the motif alphabet.";
      print "The motif file must contain a line starting with \"ALPHABET= \"";
      print "followed by 'alphabet', a list containing the letters used in";
      print "the motifs. The order of the letters in 'alphabet' must be the";
      print "same as the order of the columns of scores in the motifs.";
      exit 1;
    }
    print alpha, dataset;
    exit 0;
  }

"END"

# get the logodds matrices and stuff
$perl -ne 's/\r$//; print;' $mfile | awk -f $awk logodds=$logodds count=$count
set sav_status = $status

cleanup:
/bin/rm -f make_logodds.*.$$.tmp
exit $sav_status

---

### Post by dstew on 2008-03-18
I don't see basename called here. Maybe the best thing to do is to contact someone who was involved in development of this software. You might look on the download site for a contact person.

I don't think you are doing anything wrong on the Ubuntu side. Often, source code is written in such a way that it will only install correctly on certain Linux systems. If they did not create the software with Ubuntu in mind, then there are usually problems getting it installed.

Have you looked in Synaptic for a package that can do what you want? It looks like you are doing something with DNA or protein sequences, and I am sure there is software for that specifically for Ubuntu. Be sure to enable the Universe and Multiverse repositories (in the Settings tab) in Synaptic before looking.

---

### Post by SanHolo on 2008-03-20
> **dstew said:**
> It looks like you are doing something with DNA or protein sequences, and I am sure there is software for that specifically for Ubuntu.
There is no alternative to MEME. ;)

Just a note, MEME 3.5.7 compiles fine for me, Ubuntu (can't say which version, installed 7.04 but update all the time) and even Mac OS X. I'm sorry I have no idea what causes your problem.

---

### Post by pascale on 2008-03-20
i found the problem. i didnt have a proper c-shell. after installing csh, everything went perfect.
as sanholo wrote, meme is the closest to what i need and i dont think any other software is able to find motifs in short sequences....
anyway thanks for you help.

---

### Post by Stenico on 2008-06-19
Thanks for giving the solution! I had the same problem.

Another program you can try if you get bored with meme is Weeder:

[http://159.149.109.9/modtools/](http://159.149.109.9/modtools/)

---

