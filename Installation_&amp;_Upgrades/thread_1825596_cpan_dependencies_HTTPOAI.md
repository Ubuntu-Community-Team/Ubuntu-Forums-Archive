---
title: "cpan dependencies HTTP::OAI"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by Alex Flores on 2011-08-15
When installing the Koha, a dependency on HTTP::OAI is needed in cpan.
Running sudo cpan HTTP::OAI triggers the following:

  TIMBRODY/HTTP-OAI-3.27.tar.gz
  /usr/bin/make -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/000xml_sax.t ........... ok     
t/00static.t ............. ok     
t/01parse.t .............. ok   
t/02token.t .............. ok   
t/03badbytes.t ........... ok   
t/50mets.t ............... ok   
t/80network.t ............ ok   
t/error.t ................ ok   
t/getrecord.t ............ ok   
t/identify.t ............. ok   
t/listidentifiers.t ...... 1/3 Entity: line 3: parser error : Document is empty
<html>
     ^
# Looks like you planned 3 tests but ran 1.
# Looks like your test exited with 255 just after 1.
t/listidentifiers.t ...... Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 2/3 subtests 
t/listmetadataformats.t .. ok   


any idea? apparently in the cpantesters the GNU/Linux in 64 is FAILED. 
Is there a way to overcome this?

I installed ubuntu 11.04 (natty) with 64-bit.

Thanks

---

