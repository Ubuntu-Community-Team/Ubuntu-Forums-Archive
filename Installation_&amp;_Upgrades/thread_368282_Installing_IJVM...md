---
title: "Installing IJVM.."
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by jepsen.klaus on 2007-02-23
Hello

I'm trying to install IJVM on my desktop, and when I'm running it trow a terminal, i just get following errors...

klaus@klaus-desktop:~/Desktop/ijvm-tools-0.8$ sudo ./configure && make && make install
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for flex... (cached) flex
checking for flex... (cached) flex
checking for yywrap in -lfl... (cached) yes
checking lex output file root... (cached) lex.yy
checking whether yytext is a pointer... (cached) yes
checking for bison... (cached) bison -y
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking size of int... 32 bits
checking for vprintf... (cached) yes
creating ./config.status
creating Makefile
creating test/Makefile
Making all in .
make[1]: Entering directory `/home/klaus/Desktop/ijvm-tools-0.8'
gcc -DPACKAGE=\"ijvm-tools\" -DVERSION=\"0.8\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DHAVE_VPRINTF=1  -I. -I.   -DIJVM_DATADIR="\"/usr/local/share\""    -DCOMPILE_HOST="\"klaus-desktop\""       -DCOMPILE_DATE="\"Fri Feb 23 2007\""   -g -O2 -c ijvm-util.c
ijvm-util.c: In function ‘ijvm_image_new’:
ijvm-util.c:23: warning: incompatible implicit declaration of built-in function ‘memcpy’
gcc  -g -O2  -o ijvm-asm  ijvm-asm.o ijvm-cons.o ijvm-parse.o ijvm-lex.o ijvm-emit.o ijvm-spec.o ijvm-util.o  
gcc -DPACKAGE=\"ijvm-tools\" -DVERSION=\"0.8\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DHAVE_VPRINTF=1  -I. -I.   -DIJVM_DATADIR="\"/usr/local/share\""    -DCOMPILE_HOST="\"klaus-desktop\""       -DCOMPILE_DATE="\"Fri Feb 23 2007\""   -g -O2 -c ijvm.c
ijvm.c: In function ‘ijvm_new’:
ijvm.c:312: warning: incompatible implicit declaration of built-in function ‘memset’
ijvm.c:320: warning: incompatible implicit declaration of built-in function ‘memcpy’
gcc  -g -O2  -o ijvm  ijvm.o ijvm-util.o ijvm-spec.o  
ijvm-util.o: In function `ijvm_print_snapshot':
/home/klaus/Desktop/ijvm-tools-0.8/ijvm-util.c:205: undefined reference to `ijvm_spec'
ijvm-util.o: In function `ijvm_get_opcode':
/home/klaus/Desktop/ijvm-tools-0.8/ijvm-util.c:155: undefined reference to `ijvm_spec'
ijvm-util.o: In function `ijvm_print_init':
/home/klaus/Desktop/ijvm-tools-0.8/ijvm-util.c:146: undefined reference to `ijvm_spec'
collect2: ld returned 1 exit status
make[1]: *** [ijvm] Error 1
make[1]: Leaving directory `/home/klaus/Desktop/ijvm-tools-0.8'
make: *** [all-recursive] Error 1


- I have installed the c compiler, flex.... and all little packes that are needed.. But i still get some missing.. 

Is there anyone that can help me here ???

---

