---
title: "problem on installing install IO::Socket::SSL"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by max313 on 2010-02-11
Hello guys I want to install IO::Socket::SSL module on perl and i use this command

```
install IO::Socket::SSL
```but i got this :

```











































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































but no such parameter
SSLeay.c:3719: error: declaration for parameter ‘XS_Net__SSLeay_RAND_egd_bytes’ but no such parameter
SSLeay.c:3697: error: declaration for parameter ‘XS_Net__SSLeay_RAND_status’ but no such parameter
SSLeay.c:3675: error: declaration for parameter ‘XS_Net__SSLeay_RAND_poll’ but no such parameter
SSLeay.c:3649: error: declaration for parameter ‘XS_Net__SSLeay_RAND_add’ but no such parameter
SSLeay.c:3616: error: declaration for parameter ‘XS_Net__SSLeay_RAND_pseudo_bytes’ but no such parameter
SSLeay.c:3583: error: declaration for parameter ‘XS_Net__SSLeay_RAND_bytes’ but no such parameter
SSLeay.c:3564: error: declaration for parameter ‘XS_Net__SSLeay_ERR_load_RAND_strings’ but no such parameter
SSLeay.c:3545: error: declaration for parameter ‘XS_Net__SSLeay_ERR_load_SSL_strings’ but no such parameter
SSLeay.c:3521: error: declaration for parameter ‘XS_Net__SSLeay_ENGINE_set_default’ but no such parameter
SSLeay.c:3498: error: declaration for parameter ‘XS_Net__SSLeay_ENGINE_by_id’ but no such parameter
SSLeay.c:3479: error: declaration for parameter ‘XS_Net__SSLeay_ENGINE_register_all_complete’ but no such parameter
SSLeay.c:3460: error: declaration for parameter ‘XS_Net__SSLeay_ENGINE_load_builtin_engines’ but no such parameter
SSLeay.c:3437: error: declaration for parameter ‘XS_Net__SSLeay_library_init’ but no such parameter
SSLeay.c:3418: error: declaration for parameter ‘XS_Net__SSLeay_ERR_load_crypto_strings’ but no such parameter
SSLeay.c:3399: error: declaration for parameter ‘XS_Net__SSLeay_load_error_strings’ but no such parameter
SSLeay.c:3368: error: declaration for parameter ‘XS_Net__SSLeay_ERR_error_string’ but no such parameter
SSLeay.c:3349: error: declaration for parameter ‘XS_Net__SSLeay_ERR_clear_error’ but no such parameter
SSLeay.c:3325: error: declaration for parameter ‘XS_Net__SSLeay_ERR_put_error’ but no such parameter
SSLeay.c:3303: error: declaration for parameter ‘XS_Net__SSLeay_ERR_peek_error’ but no such parameter
SSLeay.c:3281: error: declaration for parameter ‘XS_Net__SSLeay_ERR_get_error’ but no such parameter
SSLeay.c:3259: error: declaration for parameter ‘XS_Net__SSLeay_BIO_s_mem’ but no such parameter
SSLeay.c:3237: error: declaration for parameter ‘XS_Net__SSLeay_BIO_f_ssl’ but no such parameter
SSLeay.c:3214: error: declaration for parameter ‘XS_Net__SSLeay_state’ but no such parameter
SSLeay.c:3191: error: declaration for parameter ‘XS_Net__SSLeay_want’ but no such parameter
SSLeay.c:3170: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_set_cache_size’ but no such parameter
SSLeay.c:3147: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_get_cache_size’ but no such parameter
SSLeay.c:3124: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_cache_full’ but no such parameter
SSLeay.c:3101: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_timeouts’ but no such parameter
SSLeay.c:3078: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_misses’ but no such parameter
SSLeay.c:3055: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_cb_hits’ but no such parameter
SSLeay.c:3032: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_hits’ but no such parameter
SSLeay.c:3009: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_accept_good’ but no such parameter
SSLeay.c:2986: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_accept_renegotiate’ but no such parameter
SSLeay.c:2963: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_accept’ but no such parameter
SSLeay.c:2940: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_connect_renegotiate’ but no such parameter
SSLeay.c:2917: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_connect_good’ but no such parameter
SSLeay.c:2894: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_connect’ but no such parameter
SSLeay.c:2871: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sess_number’ but no such parameter
SSLeay.c:2844: error: declaration for parameter ‘XS_Net__SSLeay_CTX_sessions’ but no such parameter
SSLeay.c:2794: error: declaration for parameter ‘XS_Net__SSLeay_CTX_set_options’ but no such parameter
SSLeay.c:2771: error: declaration for parameter ‘XS_Net__SSLeay_CTX_get_options’ but no such parameter
SSLeay.c:2750: error: declaration for parameter ‘XS_Net__SSLeay_set_options’ but no such parameter
SSLeay.c:2727: error: declaration for parameter ‘XS_Net__SSLeay_get_options’ but no such parameter
SSLeay.c:2701: error: declaration for parameter ‘XS_Net__SSLeay_CTX_ctrl’ but no such parameter
SSLeay.c:2675: error: declaration for parameter ‘XS_Net__SSLeay_ctrl’ but no such parameter
SSLeay.c:2652: error: declaration for parameter ‘XS_Net__SSLeay_get_SSL_CTX’ but no such parameter
SSLeay.c:2629: error: declaration for parameter ‘XS_Net__SSLeay_get_certificate’ but no such parameter
SSLeay.c:2606: error: declaration for parameter ‘XS_Net__SSLeay_get1_session’ but no such parameter
SSLeay.c:2582: error: declaration for parameter ‘XS_Net__SSLeay_get_session’ but no such parameter
SSLeay.c:2556: error: declaration for parameter ‘XS_Net__SSLeay_d2i_SSL_SESSION’ but no such parameter
SSLeay.c:2532: error: declaration for parameter ‘XS_Net__SSLeay_set_session’ but no such parameter
SSLeay.c:2508: error: declaration for parameter ‘XS_Net__SSLeay_i2d_SSL_SESSION’ but no such parameter
SSLeay.c:2488: error: declaration for parameter ‘XS_Net__SSLeay_SESSION_free’ but no such parameter
SSLeay.c:2464: error: declaration for parameter ‘XS_Net__SSLeay_SESSION_print’ but no such parameter
SSLeay.c:2442: error: declaration for parameter ‘XS_Net__SSLeay_SESSION_new’ but no such parameter
SSLeay.c:2419: error: declaration for parameter ‘XS_Net__SSLeay_get_wbio’ but no such parameter
SSLeay.c:2396: error: declaration for parameter ‘XS_Net__SSLeay_get_rbio’ but no such parameter
SSLeay.c:2374: error: declaration for parameter ‘XS_Net__SSLeay_set_bio’ but no such parameter
SSLeay.c:2334: error: declaration for parameter ‘XS_Net__SSLeay_set_verify’ but no such parameter
SSLeay.c:2311: error: declaration for parameter ‘XS_Net__SSLeay_get_peer_certificate’ but no such parameter
SSLeay.c:2286: error: declaration for parameter ‘XS_Net__SSLeay_get_shared_ciphers’ but no such parameter
SSLeay.c:2263: error: declaration for parameter ‘XS_Net__SSLeay_get_cipher’ but no such parameter
SSLeay.c:2239: error: declaration for parameter ‘XS_Net__SSLeay_set_cipher_list’ but no such parameter
SSLeay.c:2215: error: declaration for parameter ‘XS_Net__SSLeay_get_cipher_list’ but no such parameter
SSLeay.c:2191: error: declaration for parameter ‘XS_Net__SSLeay_CTX_set_cipher_list’ but no such parameter
SSLeay.c:2168: error: declaration for parameter ‘XS_Net__SSLeay_pending’ but no such parameter
SSLeay.c:2145: error: declaration for parameter ‘XS_Net__SSLeay_get_read_ahead’ but no such parameter
SSLeay.c:2118: error: declaration for parameter ‘XS_Net__SSLeay_set_read_ahead’ but no such parameter
SSLeay.c:2097: error: declaration for parameter ‘XS_Net__SSLeay_copy_session_id’ but no such parameter
SSLeay.c:2073: error: declaration for parameter ‘XS_Net__SSLeay_set_timeout’ but no such parameter
SSLeay.c:2050: error: declaration for parameter ‘XS_Net__SSLeay_get_timeout’ but no such parameter
SSLeay.c:2026: error: declaration for parameter ‘XS_Net__SSLeay_set_time’ but no such parameter
SSLeay.c:2003: error: declaration for parameter ‘XS_Net__SSLeay_get_time’ but no such parameter
SSLeay.c:1980: error: declaration for parameter ‘XS_Net__SSLeay_rstate_string_long’ but no such parameter
SSLeay.c:1957: error: declaration for parameter ‘XS_Net__SSLeay_state_string_long’ but no such parameter
SSLeay.c:1934: error: declaration for parameter ‘XS_Net__SSLeay_rstate_string’ but no such parameter
SSLeay.c:1911: error: declaration for parameter ‘XS_Net__SSLeay_state_string’ but no such parameter
SSLeay.c:1886: error: declaration for parameter ‘XS_Net__SSLeay_CTX_use_certificate_file’ but no such parameter
SSLeay.c:1861: error: declaration for parameter ‘XS_Net__SSLeay_use_certificate_file’ but no such parameter
SSLeay.c:1836: error: declaration for parameter ‘XS_Net__SSLeay_use_certificate_ASN1’ but no such parameter
SSLeay.c:1812: error: declaration for parameter ‘XS_Net__SSLeay_use_certificate’ but no such parameter
SSLeay.c:1787: error: declaration for parameter ‘XS_Net__SSLeay_CTX_use_PrivateKey_file’ but no such parameter
SSLeay.c:1762: error: declaration for parameter ‘XS_Net__SSLeay_use_PrivateKey_file’ but no such parameter
SSLeay.c:1736: error: declaration for parameter ‘XS_Net__SSLeay_use_PrivateKey_ASN1’ but no such parameter
SSLeay.c:1712: error: declaration for parameter ‘XS_Net__SSLeay_use_PrivateKey’ but no such parameter
SSLeay.c:1687: error: declaration for parameter ‘XS_Net__SSLeay_CTX_use_RSAPrivateKey_file’ but no such parameter
SSLeay.c:1662: error: declaration for parameter ‘XS_Net__SSLeay_use_RSAPrivateKey_file’ but no such parameter
SSLeay.c:1637: error: declaration for parameter ‘XS_Net__SSLeay_use_RSAPrivateKey_ASN1’ but no such parameter
SSLeay.c:1613: error: declaration for parameter ‘XS_Net__SSLeay_use_RSAPrivateKey’ but no such parameter
SSLeay.c:1568: error: declaration for parameter ‘XS_Net__SSLeay_write_partial’ but no such parameter
SSLeay.c:1540: error: declaration for parameter ‘XS_Net__SSLeay_write’ but no such parameter
SSLeay.c:1504: error: declaration for parameter ‘XS_Net__SSLeay_peek’ but no such parameter
SSLeay.c:1468: error: declaration for parameter ‘XS_Net__SSLeay_read’ but no such parameter
SSLeay.c:1445: error: declaration for parameter ‘XS_Net__SSLeay_get_fd’ but no such parameter
SSLeay.c:1414: error: declaration for parameter ‘XS_Net__SSLeay_set_wfd’ but no such parameter
SSLeay.c:1384: error: declaration for parameter ‘XS_Net__SSLeay_set_rfd’ but no such parameter
SSLeay.c:1354: error: declaration for parameter ‘XS_Net__SSLeay_set_fd’ but no such parameter
SSLeay.c:1232: error: declaration for parameter ‘XS_Net__SSLeay_connect’ but no such parameter
SSLeay.c:1212: error: declaration for parameter ‘XS_Net__SSLeay_clear’ but no such parameter
SSLeay.c:1189: error: declaration for parameter ‘XS_Net__SSLeay_accept’ but no such parameter
SSLeay.c:1145: error: declaration for parameter ‘XS_Net__SSLeay_free’ but no such parameter
SSLeay.c:1122: error: declaration for parameter ‘XS_Net__SSLeay_new’ but no such parameter
SSLeay.c:1097: error: declaration for parameter ‘XS_Net__SSLeay_get_error’ but no such parameter
SSLeay.c:1044: error: declaration for parameter ‘XS_Net__SSLeay_CTX_set_verify’ but no such parameter
SSLeay.c:1015: error: declaration for parameter ‘XS_Net__SSLeay_CTX_load_verify_locations’ but no such parameter
SSLeay.c:992: error: declaration for parameter ‘XS_Net__SSLeay_CTX_set_default_verify_paths’ but no such parameter
SSLeay.c:971: error: declaration for parameter ‘XS_Net__SSLeay_CTX_flush_sessions’ but no such parameter
SSLeay.c:947: error: declaration for parameter ‘XS_Net__SSLeay_CTX_remove_session’ but no such parameter
SSLeay.c:923: error: declaration for parameter ‘XS_Net__SSLeay_CTX_add_session’ but no such parameter
SSLeay.c:903: error: declaration for parameter ‘XS_Net__SSLeay_CTX_free’ but no such parameter
SSLeay.c:880: error: declaration for parameter ‘XS_Net__SSLeay_CTX_new_with_method’ but no such parameter
SSLeay.c:857: error: declaration for parameter ‘XS_Net__SSLeay_CTX_tlsv1_new’ but no such parameter
SSLeay.c:834: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v23_new’ but no such parameter
SSLeay.c:811: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v3_new’ but no such parameter
SSLeay.c:788: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v2_new’ but no such parameter
SSLeay.c:765: error: declaration for parameter ‘XS_Net__SSLeay_CTX_new’ but no such parameter
SSLeay.c:740: error: declaration for parameter ‘XS_Net__SSLeay_hello’ but no such parameter
SSLeay.c:717: error: declaration for parameter ‘XS_Net__SSLeay_constant’ but no such parameter
SSLeay.xs:366: error: declaration for parameter ‘ssleay_ctx_cert_verify_cbs’ but no such parameter
SSLeay.xs:216: error: declaration for parameter ‘ssleay_RSA_generate_key_cb_t’ but no such parameter
SSLeay.xs:215: error: declaration for parameter ‘ssleay_session_secret_cb_t’ but no such parameter
SSLeay.xs:214: error: declaration for parameter ‘ssleay_ctx_cert_verify_cb_t’ but no such parameter
SSLeay.xs:213: error: declaration for parameter ‘ssleay_ctx_passwd_cb_t’ but no such parameter
SSLeay.xs:207: error: declaration for parameter ‘ssleay_ctx_passwd_cbs’ but no such parameter
SSLeay.xs:144: error: declaration for parameter ‘ssleay_ctx_verify_callbacks’ but no such parameter
SSLeay.xs:140: error: declaration for parameter ‘perl_filehandle_t’ but no such parameter
SSLeay.c:8837: error: expected ‘{’ at end of input
make: *** [SSLeay.o] Error 1
  FLORA/Net-SSLeay-1.36.tar.gz
  /usr/bin/make -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running make for S/SU/SULLR/IO-Socket-SSL-1.31.tar.gz
  Has already been unwrapped into directory /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP

  CPAN.pm: Going to build S/SU/SULLR/IO-Socket-SSL-1.31.tar.gz

Warning: Prerequisite 'Net::SSLeay => 1.21' for 'S/SU/SULLR/IO-Socket-SSL-1.31.tar.gz' failed when processing 'F/FL/FLORA/Net-SSLeay-1.36.tar.gz' with 'make => NO'. Continuing, but chances to succeed are limited.
cp SSL.pm blib/lib/IO/Socket/SSL.pm
Manifying blib/man3/IO::Socket::SSL.3pm
  SULLR/IO-Socket-SSL-1.31.tar.gz
  /usr/bin/make -- OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/01loadmodule.............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
Compilation failed in require at t/01loadmodule.t line 14.
BEGIN failed--compilation aborted at t/01loadmodule.t line 14.
t/01loadmodule.............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
DIED. FAILED tests 1-4
    Failed 4/4 tests, 0.00% okay
t/02settings...............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
Compilation failed in require at t/02settings.t line 4.
BEGIN failed--compilation aborted at t/02settings.t line 4.
t/02settings...............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/acceptSSL-timeout........Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
Compilation failed in require at t/acceptSSL-timeout.t line 3.
BEGIN failed--compilation aborted at t/acceptSSL-timeout.t line 3.
t/acceptSSL-timeout........dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/auto_verify_hostname.....Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/auto_verify_hostname.t line 4.
BEGIN failed--compilation aborted at t/auto_verify_hostname.t line 4.
t/auto_verify_hostname.....dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/cert_no_file.............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/cert_no_file.t line 14.
BEGIN failed--compilation aborted at t/cert_no_file.t line 14.
t/cert_no_file.............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/compatibility............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
Compilation failed in require at t/compatibility.t line 5.
BEGIN failed--compilation aborted at t/compatibility.t line 5.
t/compatibility............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/connectSSL-timeout.......no testlib at t/connectSSL-timeout.t line 3.
t/connectSSL-timeout.......dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/core.....................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/core.t line 6.
BEGIN failed--compilation aborted at t/core.t line 6.
t/core.....................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/dhe......................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/dhe.t line 11.
BEGIN failed--compilation aborted at t/dhe.t line 11.
t/dhe......................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/inet6....................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/inet6.t line 5.
BEGIN failed--compilation aborted at t/inet6.t line 5.
t/inet6....................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/memleak_bad_handshake....Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/memleak_bad_handshake.t line 6.
BEGIN failed--compilation aborted at t/memleak_bad_handshake.t line 6.
t/memleak_bad_handshake....dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/nonblock.................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/nonblock.t line 6.
BEGIN failed--compilation aborted at t/nonblock.t line 6.
t/nonblock.................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/readline.................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/readline.t line 14.
BEGIN failed--compilation aborted at t/readline.t line 14.
t/readline.................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/sessions.................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/sessions.t line 5.
BEGIN failed--compilation aborted at t/sessions.t line 5.
t/sessions.................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/start-stopssl............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
BEGIN failed--compilation aborted at /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib/IO/Socket/SSL.pm line 18.
Compilation failed in require at t/start-stopssl.t line 4.
BEGIN failed--compilation aborted at t/start-stopssl.t line 4.
t/start-stopssl............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/startssl.................Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/startssl.t line 6.
BEGIN failed--compilation aborted at t/startssl.t line 6.
t/startssl.................dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/sysread_write............Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/sysread_write.t line 9.
BEGIN failed--compilation aborted at t/sysread_write.t line 9.
t/sysread_write............dubious                                           
    Test returned status 2 (wstat 512, 0x200)
t/verify_hostname..........Can't locate Net/SSLeay.pm in @INC (@INC contains: /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/lib /home/mahdi/.cpan/build/IO-Socket-SSL-1.31-FpNbyP/blib/arch /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at t/verify_hostname.t line 4.
BEGIN failed--compilation aborted at t/verify_hostname.t line 4.
t/verify_hostname..........dubious                                           
    Test returned status 2 (wstat 512, 0x200)
Failed Test               Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/01loadmodule.t             2   512     4    8  1-4
t/02settings.t               2   512    ??   ??  ??
t/acceptSSL-timeout.t        2   512    ??   ??  ??
t/auto_verify_hostname.t     2   512    ??   ??  ??
t/cert_no_file.t             2   512    ??   ??  ??
t/compatibility.t            2   512    ??   ??  ??
t/connectSSL-timeout.t       2   512    ??   ??  ??
t/core.t                     2   512    ??   ??  ??
t/dhe.t                      2   512    ??   ??  ??
t/inet6.t                    2   512    ??   ??  ??
t/memleak_bad_handshake.t    2   512    ??   ??  ??
t/nonblock.t                 2   512    ??   ??  ??
t/readline.t                 2   512    ??   ??  ??
t/sessions.t                 2   512    ??   ??  ??
t/start-stopssl.t            2   512    ??   ??  ??
t/startssl.t                 2   512    ??   ??  ??
t/sysread_write.t            2   512    ??   ??  ??
t/verify_hostname.t          2   512    ??   ??  ??
Failed 18/18 test scripts. 4/4 subtests failed.
Files=18, Tests=4,  1 wallclock secs ( 0.15 cusr +  0.11 csys =  0.26 CPU)
Failed 18/18 test programs. 4/4 subtests failed.
make: *** [test_dynamic] Error 2
  SULLR/IO-Socket-SSL-1.31.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports SULLR/IO-Socket-SSL-1.31.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force
mahdi@ubuntu:~$ ^C
mahdi@ubuntu:~$ 


```could you please help me it is so important for me i also need to install GetOpt::Long


thanks

---

### Post by max313 on 2010-02-12
someone help please

---

### Post by kkoechel on 2010-02-20
I was having the same issue.  I am using a little netbook with an atom processor.

try this: sudo apt-get libnet-ssleay-perl
then this: sudo apt-get install libssl-dev

then install Net::SSLeay on manually, cpan might work for you

got all that crap sort of from here:  [http://forums.devshed.com/perl-programming-6/module-install-failure-585932.html](http://forums.devshed.com/perl-programming-6/module-install-failure-585932.html) and here: [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)
adn here: [http://forums.theplanet.com/lofiversion/index.php/t17935.html](http://forums.theplanet.com/lofiversion/index.php/t17935.html)

Then it all worked for me

---

### Post by max313 on 2010-02-22
[sudo] password for mahdi: 
E: Invalid operation libnet-ssleay-perl
mahdi@ubuntu:~$

---

### Post by max313 on 2010-02-22
Hi again
i did what you said but i nothing changed and i get
> make: *** [pure_site_install] Error 13
  SULLR/IO-Socket-SSL-1.31.tar.gz
  /usr/bin/make install  -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state


---

### Post by gmargo on 2010-02-22
Why are you compiling this at all?  What's wrong the the version already available in the repository?

```

aptitude -V -R install libio-socket-ssl-perl libnet-ssleay-perl

```

---

### Post by max313 on 2010-02-22
i runned that command 
now what should i do?

```
[sudo] password for mahdi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libio-socket-ssl-perl [1.27-1]  
The following packages are RECOMMENDED but will NOT be installed:
  libnet-libidn-perl  
0 packages upgraded, 1 newly installed, 0 to remove and 211 not upgraded.
Need to get 57.3kB of archives. After unpacking 193kB will be used.
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com karmic/universe libio-socket-ssl-perl 1.27-1 [57.3kB]
Fetched 57.3kB in 4s (13.4kB/s)                        
Selecting previously deselected package libio-socket-ssl-perl.
(Reading database ... 116595 files and directories currently installed.)
Unpacking libio-socket-ssl-perl (from .../libio-socket-ssl-perl_1.27-1_all.deb) ...
Processing triggers for man-db ...
Setting up libio-socket-ssl-perl (1.27-1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

---

### Post by gmargo on 2010-02-22
> **max313 said:**
> I want to install IO::Socket::SSL module on perl

> **max313 said:**
> now what should i do?

IO::Socket::SSL is now installed.  Write your perl program that uses it.

See the files that were installed:
```

$ dpkg -L libio-socket-ssl-perl
/.
/usr
/usr/share
/usr/share/man
/usr/share/man/man3
/usr/share/man/man3/IO::Socket::SSL.3pm.gz
/usr/share/perl5
/usr/share/perl5/IO
/usr/share/perl5/IO/Socket
/usr/share/perl5/IO/Socket/SSL.pm
/usr/share/doc
/usr/share/doc/libio-socket-ssl-perl
/usr/share/doc/libio-socket-ssl-perl/BUGS
/usr/share/doc/libio-socket-ssl-perl/debugging.txt
/usr/share/doc/libio-socket-ssl-perl/copyright
/usr/share/doc/libio-socket-ssl-perl/changelog.gz
/usr/share/doc/libio-socket-ssl-perl/examples
/usr/share/doc/libio-socket-ssl-perl/examples/lwp-with-verifycn.pl
/usr/share/doc/libio-socket-ssl-perl/examples/ssl_client.pl
/usr/share/doc/libio-socket-ssl-perl/examples/ssl_server.pl
/usr/share/doc/libio-socket-ssl-perl/examples/async_https_server.pl.gz
/usr/share/doc/libio-socket-ssl-perl/changelog.Debian.gz

```

---

### Post by kkoechel on 2010-02-23
> **max313 said:**
> [sudo] password for mahdi: 
E: Invalid operation libnet-ssleay-perl
mahdi@ubuntu:~$

sudo apt-get libnet-ssleay-perl

should be:

sudo apt-get install libnet-ssleay-perl

---

### Post by max313 on 2010-03-06
yea it is installed
what about GetOpt::Long how can i check this

---

### Post by daqron on 2010-12-08
> **gmargo said:**
> Why are you compiling this at all?  What's wrong the the version already available in the repository?

```

aptitude -V -R install libio-socket-ssl-perl libnet-ssleay-perl

```
Win. I didn't realize this was an option. In the ancient times we had to install everything with cpan.

Cheers.

---

### Post by gmargo on 2010-12-08
A lot of the perl modules are prepackaged in the repos.  An easy way to find ones you're looking for is with **apt-cache search**:
```

$ apt-cache search IO::Socket::SSL
libevent-rpc-perl - Event based transparent Client/Server RPC framework
libhttp-daemon-ssl-perl - A simple HTTP server class with SSL support
libio-socket-ssl-perl - Perl module implementing object oriented interface to SSL sockets
libnet-imap-simple-perl - Perl module to manage an IMAP account
libnet-smtp-ssl-perl - SSL support for Net::SMTP

```

---

