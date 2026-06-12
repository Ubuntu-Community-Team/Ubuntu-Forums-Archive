---
title: "cant compile source"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by elmasry.ayman on 2010-11-18
I'm trying to install mit/gnu scheme, 
I uncompress, 
open src directory, 
./configure, 
make compile-microcode...
[B]but then i get:
[/B]cmpint.c:(.text+0x223): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_operator_1_0_trap':
cmpint.o: In function `comutil_operator_2_1_trap':
cmpint.c:(.text+0x2c7): undefined reference to `interface_to_scheme'......blablabla
**and then**
cmpintmd.c:(.text+0x477): undefined reference to `asm_generic_modulo'
`asm_sc_apply_size_2'
cmpintmd.c:(.text+0x4d4): undefined reference.... bla bla bla

what's going on??

---

### Post by wojox on 2010-11-18
You followed this [MIT/GNU Scheme]("http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user/Unix-Installation.html") ?

---

### Post by elmasry.ayman on 2010-11-18
yes i did

---

### Post by mempman on 2010-11-18
try the following:

$ sudo apt-get install build-essentials
$ cd src directory; ./configure ; make

post ur output if above fails

---

### Post by elmasry.ayman on 2010-11-18
> **mempman said:**
> try the following:

$ sudo apt-get install build-essentials
$ cd src directory; ./configure ; make

post ur output if above fails

I didn't find build-essentials, but I found build-essential with no 's'. I installed it and the make command still gives me the same errors:
```
(cd microcode && make all)
make[1]: Entering directory `/home/ayman/Downloads/mit-scheme-9.0.1/src/microcode'
rm -f usrdef.c
./findprim artutl.c avltree.c bkpt.c bignum.c bigprm.c bitstr.c boot.c char.c daemon.c debug.c dfloat.c error.c extern.c fasdump.c fasl.c fasload.c fixnum.c flonum.c gcloop.c generic.c hooks.c hunk.c intern.c interp.c intprm.c list.c lookprm.c lookup.c memmag.c missing.c obstack.c option.c osscheme.c ostty.c outf.c prim.c primutl.c ptrvec.c purify.c purutl.c regex.c rgxprim.c step.c storage.c string.c syntax.c sysprim.c term.c transact.c tterm.c utabmd.c utils.c vector.c wind.c prosenv.c prosfile.c prosfs.c prosio.c prosproc.c prospty.c prosterm.c prostty.c pruxsock.c intext.c pruxenv.c pruxfs.c pruxio.c ux.c uxctty.c uxenv.c uxfile.c uxfs.c uxio.c uxproc.c uxsig.c uxsock.c uxterm.c uxtop.c uxtrap.c uxtty.c uxutil.c cmpauxmd.m4 termcap.c tparam.c pruxdld.c cmpint.c cmpintmd.c comutl.c > usrdef.c
gcc -DHAVE_CONFIG_H -DMIT_SCHEME -DDEFAULT_LIBRARY_PATH=\"/usr/local/lib/mit-scheme-x86-64\" -I. -I. -O3 -Wall -Wundef -Wpointer-arith -Winline -Wstrict-prototypes -Wnested-externs -Wredundant-decls -Wextra -Wno-sign-compare -Wno-unused-parameter -Wold-style-definition -o usrdef.o -c usrdef.c
rm -f scheme
gcc  -o scheme -export-dynamic artutl.o avltree.o bkpt.o bignum.o bigprm.o bitstr.o boot.o char.o daemon.o debug.o dfloat.o error.o extern.o fasdump.o fasl.o fasload.o fixnum.o flonum.o gcloop.o generic.o hooks.o hunk.o intern.o interp.o intprm.o list.o lookprm.o lookup.o memmag.o missing.o obstack.o option.o osscheme.o ostty.o outf.o prim.o primutl.o ptrvec.o purify.o purutl.o regex.o rgxprim.o step.o storage.o string.o syntax.o sysprim.o term.o transact.o tterm.o utabmd.o utils.o vector.o wind.o prosenv.o prosfile.o prosfs.o prosio.o prosproc.o prospty.o prosterm.o prostty.o pruxsock.o intext.o pruxenv.o pruxfs.o pruxio.o ux.o uxctty.o uxenv.o uxfile.o uxfs.o uxio.o uxproc.o uxsig.o uxsock.o uxterm.o uxtop.o uxtrap.o uxtty.o uxutil.o cmpauxmd.o termcap.o tparam.o pruxdld.o cmpint.o cmpintmd.o comutl.o usrdef.o  -ldl -lm 
cmpint.o: In function `comutil_return_to_interpreter':
cmpint.c:(.text+0x223): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_operator_1_0_trap':
cmpint.c:(.text+0x23d): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_2_0_trap':
cmpint.c:(.text+0x287): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_2_1_trap':
cmpint.c:(.text+0x2c7): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_3_0_trap':
cmpint.c:(.text+0x317): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_3_1_trap':
cmpint.c:(.text+0x367): undefined reference to `interface_to_scheme'
cmpint.o:cmpint.c:(.text+0x3b7): more undefined references to `interface_to_scheme' follow
cmpint.o: In function `return_to_compiled_code':
cmpint.c:(.text+0xd41): undefined reference to `C_to_interface'
cmpint.o: In function `comutil_primitive_error':
cmpint.c:(.text+0xdb8): undefined reference to `interface_to_C'
cmpint.o: In function `compiler_interrupt_common':
cmpint.c:(.text+0x14a0): undefined reference to `interface_to_C'
cmpint.o: In function `comp_unassigned_p_trap_restart':
cmpint.c:(.text+0x16dd): undefined reference to `C_to_interface'
cmpint.o: In function `comp_safe_lookup_trap_restart':
cmpint.c:(.text+0x17fd): undefined reference to `C_to_interface'
cmpint.o: In function `comp_lookup_trap_restart':
cmpint.c:(.text+0x191d): undefined reference to `C_to_interface'
cmpint.o: In function `comp_assignment_trap_restart':
cmpint.c:(.text+0x1a4d): undefined reference to `C_to_interface'
cmpint.o: In function `comutil_primitive_lexpr_apply':
cmpint.c:(.text+0x1da6): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_primitive_apply':
cmpint.c:(.text+0x1eb9): undefined reference to `interface_to_scheme'
cmpint.o: In function `enter_compiled_expression':
cmpint.c:(.text+0x219d): undefined reference to `C_to_interface'
cmpint.o: In function `comp_op_lookup_trap_restart':
cmpint.c:(.text+0x2644): undefined reference to `C_to_interface'
cmpint.o: In function `comutil_unassigned_p_trap':
cmpint.c:(.text+0x2747): undefined reference to `interface_to_scheme'
cmpint.c:(.text+0x2850): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_assignment_trap':
cmpint.c:(.text+0x28bd): undefined reference to `interface_to_scheme'
cmpint.c:(.text+0x29e2): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_safe_lookup_trap':
cmpint.c:(.text+0x2a47): undefined reference to `interface_to_scheme'
cmpint.c:(.text+0x2b50): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_link':
cmpint.c:(.text+0x2c62): undefined reference to `interface_to_C'
cmpint.c:(.text+0x2c85): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_lookup_trap':
cmpint.c:(.text+0x2cf7): undefined reference to `interface_to_scheme'
cmpint.c:(.text+0x2e00): undefined reference to `interface_to_C'
cmpint.o: In function `comp_link_caches_restart':
cmpint.c:(.text+0x2fdb): undefined reference to `C_to_interface'
cmpint.o: In function `comutil_operator_lexpr_trap':
cmpint.c:(.text+0x32eb): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_primitive_trap':
cmpint.c:(.text+0x33f9): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_lexpr_apply':
cmpint.c:(.text+0x3d31): undefined reference to `interface_to_C'
cmpint.c:(.text+0x3d8d): undefined reference to `interface_to_C'
cmpint.c:(.text+0x3ddc): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_apply':
cmpint.c:(.text+0x44d1): undefined reference to `interface_to_C'
cmpint.c:(.text+0x4641): undefined reference to `interface_to_C'
cmpint.c:(.text+0x46a6): undefined reference to `interface_to_C'
cmpint.c:(.text+0x46ee): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_operator_lookup_trap':
cmpint.c:(.text+0x4a70): undefined reference to `interface_to_C'
cmpint.o: In function `comutil_reflect_to_interface':
cmpint.c:(.text+0x4b37): undefined reference to `interface_to_C'
cmpint.c:(.text+0x4b95): undefined reference to `interface_to_C'
cmpint.c:(.text+0x4c2e): undefined reference to `interface_to_scheme'
cmpint.c:(.text+0x4c76): undefined reference to `interface_to_scheme'
cmpint.o: In function `comutil_cache_lookup_apply':
cmpint.c:(.text+0x50c8): undefined reference to `interface_to_C'
cmpint.o: In function `comp_cache_lookup_apply_restart':
cmpint.c:(.text+0x53a7): undefined reference to `C_to_interface'
cmpint.o: In function `comp_error_restart':
cmpint.c:(.text+0xc27): undefined reference to `C_to_interface'
cmpint.o: In function `comp_interrupt_restart':
cmpint.c:(.text+0xc88): undefined reference to `C_to_interface'
cmpint.o: In function `apply_compiled_procedure':
cmpint.c:(.text+0x43ad): undefined reference to `C_to_interface'
cmpintmd.o: In function `x86_64_reset_hook':
cmpintmd.c:(.text+0x17a): undefined reference to `asm_scheme_to_interface'
cmpintmd.c:(.text+0x185): undefined reference to `asm_scheme_to_interface'
cmpintmd.c:(.text+0x194): undefined reference to `asm_scheme_to_interface_call'
cmpintmd.c:(.text+0x19f): undefined reference to `asm_scheme_to_interface_call'
cmpintmd.c:(.text+0x1ae): undefined reference to `asm_trampoline_to_interface'
cmpintmd.c:(.text+0x1b9): undefined reference to `asm_trampoline_to_interface'
cmpintmd.c:(.text+0x1c8): undefined reference to `asm_interrupt_procedure'
cmpintmd.c:(.text+0x1d3): undefined reference to `asm_interrupt_procedure'
cmpintmd.c:(.text+0x1e2): undefined reference to `asm_interrupt_continuation'
cmpintmd.c:(.text+0x1ed): undefined reference to `asm_interrupt_continuation'
cmpintmd.c:(.text+0x1fc): undefined reference to `asm_interrupt_closure'
cmpintmd.c:(.text+0x207): undefined reference to `asm_interrupt_closure'
cmpintmd.c:(.text+0x216): undefined reference to `asm_interrupt_dlink'
cmpintmd.c:(.text+0x221): undefined reference to `asm_interrupt_dlink'
cmpintmd.c:(.text+0x230): undefined reference to `asm_primitive_apply'
cmpintmd.c:(.text+0x23b): undefined reference to `asm_primitive_apply'
cmpintmd.c:(.text+0x24a): undefined reference to `asm_primitive_lexpr_apply'
cmpintmd.c:(.text+0x255): undefined reference to `asm_primitive_lexpr_apply'
cmpintmd.c:(.text+0x264): undefined reference to `asm_assignment_trap'
cmpintmd.c:(.text+0x26f): undefined reference to `asm_assignment_trap'
cmpintmd.c:(.text+0x27e): undefined reference to `asm_reference_trap'
cmpintmd.c:(.text+0x289): undefined reference to `asm_reference_trap'
cmpintmd.c:(.text+0x298): undefined reference to `asm_safe_reference_trap'
cmpintmd.c:(.text+0x2a3): undefined reference to `asm_safe_reference_trap'
cmpintmd.c:(.text+0x2b2): undefined reference to `asm_link'
cmpintmd.c:(.text+0x2bd): undefined reference to `asm_link'
cmpintmd.c:(.text+0x2cc): undefined reference to `asm_error'
cmpintmd.c:(.text+0x2d7): undefined reference to `asm_error'
cmpintmd.c:(.text+0x2e6): undefined reference to `asm_primitive_error'
cmpintmd.c:(.text+0x2f1): undefined reference to `asm_primitive_error'
cmpintmd.c:(.text+0x300): undefined reference to `asm_generic_add'
cmpintmd.c:(.text+0x30b): undefined reference to `asm_generic_add'
cmpintmd.c:(.text+0x31a): undefined reference to `asm_generic_subtract'
cmpintmd.c:(.text+0x325): undefined reference to `asm_generic_subtract'
cmpintmd.c:(.text+0x334): undefined reference to `asm_generic_multiply'
cmpintmd.c:(.text+0x33f): undefined reference to `asm_generic_multiply'
cmpintmd.c:(.text+0x34e): undefined reference to `asm_generic_divide'
cmpintmd.c:(.text+0x359): undefined reference to `asm_generic_divide'
cmpintmd.c:(.text+0x368): undefined reference to `asm_generic_equal'
cmpintmd.c:(.text+0x373): undefined reference to `asm_generic_equal'
cmpintmd.c:(.text+0x382): undefined reference to `asm_generic_less'
cmpintmd.c:(.text+0x38d): undefined reference to `asm_generic_less'
cmpintmd.c:(.text+0x39c): undefined reference to `asm_generic_greater'
cmpintmd.c:(.text+0x3a7): undefined reference to `asm_generic_greater'
cmpintmd.c:(.text+0x3b6): undefined reference to `asm_generic_increment'
cmpintmd.c:(.text+0x3c1): undefined reference to `asm_generic_increment'
cmpintmd.c:(.text+0x3d0): undefined reference to `asm_generic_decrement'
cmpintmd.c:(.text+0x3db): undefined reference to `asm_generic_decrement'
cmpintmd.c:(.text+0x3ea): undefined reference to `asm_generic_zero'
cmpintmd.c:(.text+0x3f5): undefined reference to `asm_generic_zero'
cmpintmd.c:(.text+0x404): undefined reference to `asm_generic_positive'
cmpintmd.c:(.text+0x40f): undefined reference to `asm_generic_positive'
cmpintmd.c:(.text+0x41e): undefined reference to `asm_generic_negative'
cmpintmd.c:(.text+0x429): undefined reference to `asm_generic_negative'
cmpintmd.c:(.text+0x438): undefined reference to `asm_generic_quotient'
cmpintmd.c:(.text+0x443): undefined reference to `asm_generic_quotient'
cmpintmd.c:(.text+0x452): undefined reference to `asm_generic_remainder'
cmpintmd.c:(.text+0x45d): undefined reference to `asm_generic_remainder'
cmpintmd.c:(.text+0x46c): undefined reference to `asm_generic_modulo'
cmpintmd.c:(.text+0x477): undefined reference to `asm_generic_modulo'
cmpintmd.c:(.text+0x486): undefined reference to `asm_sc_apply'
cmpintmd.c:(.text+0x491): undefined reference to `asm_sc_apply'
cmpintmd.c:(.text+0x4a0): undefined reference to `asm_sc_apply_size_1'
cmpintmd.c:(.text+0x4ab): undefined reference to `asm_sc_apply_size_1'
cmpintmd.c:(.text+0x4ba): undefined reference to `asm_sc_apply_size_2'
cmpintmd.c:(.text+0x4c5): undefined reference to `asm_sc_apply_size_2'
cmpintmd.c:(.text+0x4d4): undefined reference to `asm_sc_apply_size_3'
cmpintmd.c:(.text+0x4df): undefined reference to `asm_sc_apply_size_3'
cmpintmd.c:(.text+0x4ee): undefined reference to `asm_sc_apply_size_4'
cmpintmd.c:(.text+0x4f9): undefined reference to `asm_sc_apply_size_4'
cmpintmd.c:(.text+0x508): undefined reference to `asm_sc_apply_size_5'
cmpintmd.c:(.text+0x513): undefined reference to `asm_sc_apply_size_5'
cmpintmd.c:(.text+0x522): undefined reference to `asm_sc_apply_size_6'
cmpintmd.c:(.text+0x52d): undefined reference to `asm_sc_apply_size_6'
cmpintmd.c:(.text+0x53c): undefined reference to `asm_sc_apply_size_7'
cmpintmd.c:(.text+0x547): undefined reference to `asm_sc_apply_size_7'
cmpintmd.c:(.text+0x556): undefined reference to `asm_sc_apply_size_8'
cmpintmd.c:(.text+0x561): undefined reference to `asm_sc_apply_size_8'
cmpintmd.c:(.text+0x570): undefined reference to `asm_interrupt_continuation_2'
cmpintmd.c:(.text+0x57b): undefined reference to `asm_interrupt_continuation_2'
cmpintmd.c:(.text+0x58b): undefined reference to `asm_fixnum_shift'
cmpintmd.c:(.text+0x595): undefined reference to `asm_fixnum_shift'
collect2: ld returned 1 exit status
make[1]: *** [scheme] Error 1
make[1]: Leaving directory `/home/ayman/Downloads/mit-scheme-9.0.1/src/microcode'
make: *** [compile-microcode] Error 2

```

---

### Post by leaonfm on 2011-01-04
:lolflag: the compile process failed because you need to have a package called "m4" install first, that's the only piece you absolutely must-have before you go about compiling the mit-scheme src
So:
```
sudo apt-get install m4
```
then start from scratch, it should work.

---

### Post by elmasry.ayman on 2011-01-04
> **leaonfm said:**
> :lolflag: the compile process failed because you need to have a package called "m4" install first, that's the only piece you absolutely must-have before you go about compiling the mit-scheme src
So:
```
sudo apt-get install m4
```
then start from scratch, it should work.

hmmm... OK I'll try it.

---

