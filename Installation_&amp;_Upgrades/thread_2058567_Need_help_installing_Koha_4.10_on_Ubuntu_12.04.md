---
title: "Need help installing Koha 4.10 on Ubuntu 12.04"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by chaud245 on 2012-09-16
I am trying to help my school by setting up an open source replacement for our current OPAC system and I've decided on Koha. following the README/Install documents instructions I have reach a step where I use perl to run file labeled Makefile.PL and at the end of this command I get a list of errors could someone give me a solution/command(s)? And I know this list is fairly extensive so sorry and thank you in advance.
[U]Koha INSTALL "README"
[/U][https://github.com/liblime/LibLime-Koha/blob/4_10/INSTALL](https://github.com/liblime/LibLime-Koha/blob/4_10/INSTALL) 

> Warning: prerequisite Algorithm::CheckDigits 0.5 not found.
Warning: prerequisite Biblio::EndnoteStyle 0.05 not found.
Warning: prerequisite Business::ISBN 2.05 not found.
Warning: prerequisite CGI::Compile 0.15 not found.
Warning: prerequisite CGI::Emulate::PSGI 0.14 not found.
Warning: prerequisite CGI::Session 4.2 not found.
Warning: prerequisite CGI::Session::Serialize::yaml 4.2 not found.
Warning: prerequisite CHI 0.49 not found.
Warning: prerequisite Cache::Memcached 1.24 not found.
Warning: prerequisite Cache::Memcached::Fast 0.19 not found.
Warning: prerequisite Class::Accessor 0.3 not found.
Warning: prerequisite Class::Factory::Util 1.6 not found.
Warning: prerequisite Clone 0.31 not found.
Warning: prerequisite DBD::SQLite 0.33 not found.
Warning: prerequisite DBIx::Connector 0.47 not found.
Warning: prerequisite Data::ICal 0.13 not found.
Warning: prerequisite Date::Calc 5.4 not found.
Warning: prerequisite Date::ICal 1.72 not found.
Warning: prerequisite Date::Manip 5.44 not found.
Warning: prerequisite DateTime 0.65 not found.
Warning: prerequisite DateTime::Format::DateParse 0.05 not found.
Warning: prerequisite DateTime::Format::Strptime 1.5 not found.
Warning: prerequisite Email::Date 1.103 not found.
Warning: prerequisite File::Slurp 9999.13 not found.
Warning: prerequisite GD 2.39 not found.
Warning: prerequisite GD::Barcode::UPCE 1.1 not found.
Warning: prerequisite HTML::Scrubber 0.08 not found.
Warning: prerequisite HTML::Template::Pro 0.69 not found.
Warning: prerequisite HTTP::Cookies 1.39 not found.
Warning: prerequisite HTTP::Exception 0.03001 not found.
Warning: prerequisite HTTP::OAI 3.2 not found.
Warning: prerequisite HTTP::Request::Common 1.26 not found.
Warning: prerequisite JSON 2.07 not found.
Warning: prerequisite LWP::Simple 1.41 not found.
Warning: prerequisite LWP::UserAgent 2.033 not found.
Warning: prerequisite Lingua::Stem 0.82 not found.
Warning: prerequisite List::MoreUtils 0.21 not found.
Warning: prerequisite MARC::Charset 0.98 not found.
Warning: prerequisite MARC::Crosswalk::DublinCore 0.02 not found.
Warning: prerequisite MARC::File::XML 0.88 not found.
Warning: prerequisite MARC::Record 2 not found.
Warning: prerequisite MIME::Lite 3 not found.
Warning: prerequisite Mail::Sendmail 0.79 not found.
Warning: prerequisite Memoize::Memcached 0.03 not found.
Warning: prerequisite Modern::Perl 1.03 not found.
Warning: prerequisite Moose 2.0006 not found.
Warning: prerequisite MooseX::Role::Parameterized 0.26 not found.
Warning: prerequisite Net::IP 1.25 not found.
Warning: prerequisite Net::LDAP 0.33 not found.
Warning: prerequisite Net::LDAP::Filter 0.14 not found.
Warning: prerequisite Net::Server::PreFork 0.97 not found.
Warning: prerequisite Net::Z3950::ZOOM 1.16 not found.
Warning: prerequisite PDF::API2 2 not found.
Warning: prerequisite PDF::API2::Page 2 not found.
Warning: prerequisite PDF::API2::Util 2 not found.
Warning: prerequisite PDF::Reuse 0.33 not found.
Warning: prerequisite PDF::Reuse::Barcode 0.05 not found.
Warning: prerequisite POE 0.9999 not found.
Warning: prerequisite Plack 0.9978 not found.
Warning: prerequisite Plack::Middleware::Deflater 0.03 not found.
Warning: prerequisite Plack::Middleware::Expires 0.03 not found.
Warning: prerequisite Plack::Middleware::HTTPExceptions 0.01 not found.
Warning: prerequisite Plack::Middleware::Header 0.04 not found.
Warning: prerequisite Plack::Middleware::MethodOverride 0.1 not found.
Warning: prerequisite Plack::Middleware::ReverseProxy 0.09 not found.
Warning: prerequisite Plack::Middleware::Rewrite 1.003 not found.
Warning: prerequisite Plack::Middleware::Status 1.10115 not found.
Warning: prerequisite Rose::DB 0.762 not found.
Warning: prerequisite Rose::DB::Object 0.791 not found.
Warning: prerequisite Rose::DB::Object::Helpers 0.784 not found.
Warning: prerequisite Rose::DB::Object::Loader 0.787 not found.
Warning: prerequisite SMS::Send 0.05 not found.
Warning: prerequisite Schedule::At 1.06 not found.
Warning: prerequisite Squatting 0.81 not found.
Warning: prerequisite Squatting::On::PSGI 0.06 not found.
Warning: prerequisite Text::Aspell 0.04 not found.
Warning: prerequisite Text::CSV 0.01 not found.
Warning: prerequisite Text::CSV_XS 0.32 not found.
Warning: prerequisite Try::Tiny 0.06 not found.
Warning: prerequisite URI::Escape 1.36 not found.
Warning: prerequisite XML::Dumper 0.81 not found.
Warning: prerequisite XML::LibXML 1.59 not found.
Warning: prerequisite XML::LibXSLT 1.59 not found.
Warning: prerequisite XML::RSS 1.31 not found.
Warning: prerequisite XML::SAX::ExpatXS 1.31 not found.
Warning: prerequisite XML::SAX::ParserFactory 1.01 not found.
Warning: prerequisite XML::SAX::Writer 0.44 not found.
Warning: prerequisite XML::Simple 2.14 not found.
Warning: prerequisite YAML::Syck 0.71 not found.
Writing Makefile for koha
Writing MYMETA.yml


---

### Post by chaud245 on 2012-10-09
I finally got it installed. I found the wiki guide for packages install.

---

### Post by mrliambi on 2012-10-09
> **chaud245 said:**
> I finally got it installed. I found the wiki guide for packages install.
If you don't mind would you please share your solution with me, cause i have the same problem, or post a link to the wiki you found that helped you solve the problem. Thank you.

---

### Post by chaud245 on 2012-10-10
I have done my best to create some form of an installation guide that uses the packages system. My guide was based on a fresh install of Ubuntu Server 12.04.1 and it is possible that updating the system before following this guide could produce different results (sorta like my disclaimer).
 
Google Docs link to my guide, let me know if it has issues.
[https://docs.google.com/open?id=0BytcL_Hx8-Y9eXRaNnJRQ0ctUms](https://docs.google.com/open?id=0BytcL_Hx8-Y9eXRaNnJRQ0ctUms)

---

