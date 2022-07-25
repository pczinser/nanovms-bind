## NanoVMS Named

This package is the BIND DNS server named in a nanovms unikernel.


If you run into problems you can submit an issue at https://github.com/pczinser/nanovms-bind .

## Configuration:

By default this will run the DNS server on port 53. If you want to test and already have something listening on 53 you will need to change that in the package.manifest or with a config.json

```
{
  "Args": ["named", "-p", "8053", "-4", "-g", "-f"]
}
```


To update your named.conf create a new directory locally:

```
$ mkdir -p usr/local/etc/
```

Place your named.conf in there.

Then include the directory using this config.json stanza:

```
{
  "Dirs": ["usr"]
}
```

## Testing

```
$ ops load named_9.18.6
```
If you are testing locally and have changed the default port:

```
$ ops load named_9.18.6 -p 8053

$ dig @127.0.0.1 -p 8053 nanovms.com ANY +tcp
```
