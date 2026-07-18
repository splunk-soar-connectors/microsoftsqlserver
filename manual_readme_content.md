This app will ignore the HTTP_PROXY and HTTPS_PROXY environment variables, as it does not use HTTP
to connect to the database.\
Below are the default ports used by Microsoft-SQL-Server.

|         Service Name | Port | Transport Protocol |
|----------------------------------------------|------|--------------------|
|          **Microsoft-SQL-Server (ms-sql-s)** | 1433 | tcp |
|          **Microsoft-SQL-Server (ms-sql-s)** | 1433 | udp |

## TLS certificate verification

The connector requires TLS and verifies the SQL Server certificate and configured hostname by
default. Set **CA file** to a PEM bundle when the server uses a private certificate authority. The
default value, `system`, uses the operating system trust store.

Disabling **Verify server certificate** is an explicit compatibility opt-out. It keeps the database
traffic encrypted when **Encryption** is `require`, but it does not authenticate the remote server
and can expose credentials and data to a man-in-the-middle attacker. Setting **Encryption** to `off`
also disables transport encryption.

## LGPL

This app uses the pymssql module, which is licensed under the Free Software Foundation (FSF).

## Notice for usage on RHEL FIPS system

You might have to follow the instructions [here](https://access.redhat.com/solutions/7035895)
and remove pymssql dependency found in \<path_to_phantom>/apps/microsoftsqlserver\_\*/dependencies
on your instance or downgrade to an earlier version to use this connector on RHEL system with FIPS enabled
