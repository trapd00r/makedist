[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=65SFZJ25PSKG8&currency_code=SEK&source=url) - Every tiny cent helps a lot!

# makedist - make cpan distribution

# USAGE

    makedist [OPTIONS]

# DESCRIPTION

makedist automates the process of creating a distribution to be
uploaded to CPAN.

The MANIFEST file is inspected for files to be included.

We make an attempt to extract the package name from any perl module
file found, and the package name must follow this convention:

    package File::LsColor;

If extraction fails, we use the basename of the current working
directory as a distribution name:

    ~/dev/File-LsColor  => File-LsColor

Version number is extracted from a perl module file if it exists, else
an App:: distribution is assumed and version is extracted from the bin/
directory.

# CONFIGURATION

Various options can be set in the makedist.conf configuration file, located in
$XDG\_CONFIG\_HOME/makedist/makedist.conf.

By default, two variables can be accessed and modified in the
configuration file:

    # the basename of the gzipped tarball, i.e File-LsColor-0.192.tar.gz
    $finished_product

    # code to execute on success. A few examples are provided in the
    # configuration file.
    $command_on_success

The author uses the $command\_on\_success coderef like this:

    our $command_on_success = sub {
      copy();   # copy the dist to a local dir
      scp();    # scp the dist to a remote server
      upload(); # upload the dist to cpan
    }

An example configuration file is provided with this distribution.

# OPTIONS

    -v, --verbose explain what is being done
    -h, --help    show this help and exit

# REPORTING BUGS

Report bugs and/or feature requests on [https://github.com/trapd00r/makedist](https://github.com/trapd00r/makedist),
the repository issue tracker or directly to [m@japh.se](https://metacpan.org/pod/m@japh.se)

# AUTHOR

    Magnus Woldrich
    CPAN ID: WOLDRICH
    m@japh.se
    http://japh.se
    http://github.com/trapd00r

# CONTRIBUTORS

None required yet.

# COPYRIGHT

Copyright 2018 **THIS APPLICATION**s ["AUTHOR"](#author) and ["CONTRIBUTORS"](#contributors) as listed
above.

# LICENSE

This program is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO

[~/](http://japh.se)
