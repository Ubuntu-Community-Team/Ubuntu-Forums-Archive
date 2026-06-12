---
title: "NS2 otcl problem"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by adnan_s on 2010-04-01
Hy, I've downloaded the ''ns-allinone-2.34''.

I've make a directory in my home folder and past the source files there.

When I make the installation I become this message:

otcl.o: In function `OTclDispatch':
/home/adnan/ns2_adnan/ns-allinone-2.34/otcl-1.13/otcl.c:495: undefined reference to `__stack_chk_fail_local'
otcl.o: In function `Otcl_Init':
/home/adnan/ns2_adnan/ns-allinone-2.34/otcl-1.13/otcl.c:2284: undefined reference to `__stack_chk_fail_local'
ld: libotcl.so: hidden symbol `__stack_chk_fail_local' isn't defined
ld: final link failed: Nonrepresentable section on output
make: *** [libotcl.so] Error 1
otcl-1.13 make failed! Exiting ...
See [http://www.isi.edu/nsnam/ns/ns-problems.html](http://www.isi.edu/nsnam/ns/ns-problems.html) for problems
adnan@adnan-laptop:~/ns2_adnan/ns-allinone-2.34$ 

I really need this simulator, also when someone are able to help me
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by mirza_farid on 2010-06-14
hi

i have somethings like that
you should change your makefile.in in otcl folder
line 7 change the "CC" to "gcc-4.3"
not the "CC" ! something wroten in front of the "CC"
you can also change the user to the "root"
change the password and use the "root" user
it's the administrator

good like

---

### Post by mirza_farid on 2010-06-20
does it work for you?

---

### Post by tomneb on 2010-08-03
Hi mirza_farid,

I have the exact same problem and your tip did not worked.
Do you have any other idea?

Thanks for replay!

---

### Post by Sushanta-NS3 on 2011-01-23
Hi tomneb and adnan_s,

If you are still having the problem then you can try the following. I faced the same problem and could fix it in the following way:

1. Locate the configure.in file in the otcl folder of ns-allinone-2.34.
2. Open it using your favorite editor.
3. Locate the following lines:

    ;;
     Linux*)
         SHLIB_CFLAGS="-fpic"
         SHLIB_LD="ld -shared"
         SHLIB_SUFFIX=".so"
         DL_LIBS="-ldl"
         SHLD_FLAGS=""

4. Add the following line after SHLIB_LD="ld -shared"

    SHLIB_LD="${CC} -shared"

5. In the terminal navigate to the otcl folder under ns-allinone-2.34.
6. Issue autoconf.
7. If autoconf is not installed you can use sudo apt-get install autoconf2.13
8. Once autoconf is done issue ./configue and then make.

This should successfully install OTcl.

---

