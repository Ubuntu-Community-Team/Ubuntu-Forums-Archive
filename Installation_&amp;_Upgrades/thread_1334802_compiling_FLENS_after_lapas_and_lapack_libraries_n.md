---
title: "compiling FLENS after lapas and lapack libraries names were changed ??"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by mohabic on 2009-11-22
Ubuntu/Linux:- Packages (libraries) names were changed, now i've errors in "making" the library. ?!?
this line was to install dependencies 
apt-get install atlas3-base atlas3-headers lapack3-pic refblas3-dev

it didnt work, so i asked some people and they told that these libraries' names were changed, thus this line worked succesfully:-
apt-get install libatlas-base-dev liblapack-pic

the problem now, when i "make" another library called FLENS, (the last 2 libraries are its dependencies), i get this error
----------------------------------
moha@ubuntu:~$ cd /home/moha/FLENS/
moha@ubuntu:~/FLENS$ make

FLENS_HOME=/home/moha/FLENS


processing dir flens:

make[1]: Entering directory `/home/moha/FLENS/flens'
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/aux_complex.o -c aux_complex.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/blas.o -c blas.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/id.o -c id.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/lapack.o -c lapack.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/range.o -c range.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/refcounter.o -c refcounter.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/scalarclosures.o -c scalarclosures.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/snapshot.o -c snapshot.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/sparse_blas.o -c sparse_blas.cc
g++ -I /home/moha/FLENS -I/sw/include -I. -Wall -Wextra -Werror -g -O3 -fPIC -o .obj/underscore.o -c underscore.cc
g++ -shared -Wall -Wextra -Werror -g -O3 -fPIC -o libflens.so .obj/*.o -llapack -latlas -lblas
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/moha/FLENS/flens'

processing dir tutorials:

make[1]: Entering directory `/home/moha/FLENS/tutorials'
g++ -Wall -Wextra -Werror -g -O3 -fPIC -I /home/moha/FLENS -I/sw/include -I. -I . -o s01_t01_gematrix.o -c s01_t01_gematrix.cc
g++ -o s01_t01_gematrix s01_t01_gematrix.o -L.. -lflens -llapack -latlas -lblas 
/usr/bin/ld: cannot find -lflens
collect2: ld returned 1 exit status
make[1]: *** [s01_t01_gematrix] Error 1
make[1]: Leaving directory `/home/moha/FLENS/tutorials'

processing dir examples:

make[1]: Entering directory `/home/moha/FLENS/examples'
g++ -Wall -Wextra -Werror -g -O3 -fPIC -I /home/moha/FLENS -I/sw/include -I. -I . -o coarsegridcorrection coarsegridcorrection.cc -L.. -lflens -llapack -latlas -lblas 
/usr/bin/ld: cannot find -lflens
collect2: ld returned 1 exit status
make[1]: *** [coarsegridcorrection] Error 1
make[1]: Leaving directory `/home/moha/FLENS/examples'

processing dir tests:

make[1]: Entering directory `/home/moha/FLENS/tests'
g++ -Wall -Wextra -Werror -g -O3 -fPIC -I /home/moha/FLENS -I/sw/include -I. -I . -o sparsegematrix sparsegematrix.cc -L.. -lflens -llapack -latlas -lblas 
/usr/bin/ld: cannot find -lflens
collect2: ld returned 1 exit status
make[1]: *** [sparsegematrix] Error 1
make[1]: Leaving directory `/home/moha/FLENS/tests'
make: *** [all] Error 2
-----------------------------------

i guess the error is in the files that respond to make instruction, well
the question is which file(s) should i find in and repair them ???
and what should i replace also ?

Thanks on advance
(linux amateur)

---

