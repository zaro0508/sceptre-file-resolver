# File Resolver

A Sceptre resolver to get file contents. The returned value that gets
passed to the parameter can be a string, json, or yaml object.  The
file extension determines the return type.

## Syntax:

```yaml
parameters|sceptre_user_data:
  <name>: !file /path/to/local/file
```

```yaml
parameters|sceptre_user_data:
  <name>: !file URL/To/File
```

## Examples

### Local file

#### string
Get file content and pass it to the parameter as a string:

tags/departments.txt
```
"HR, Governance, Engineering, Marketing"
```

```yaml
parameters:
  departments: !file tags/departments.txt
```

#### json
Get file contents and pass it to the parameter as a json object:

tags/departments.json
```yaml
[
  "HR",
  "Governance",
  "Engineering",
  "Marketing"
]
```

```yaml
parameters:
  departments: !file tags/departments.json
```

#### yaml
Get file contents and pass it to the sceptre_user_data as a yaml object:

tags/departments.yaml
```yaml
- "HR"
- "Governance"
- "Engineering"
- "Marketing"
```

```yaml
sceptre_user_data:
  departments: !file tags/departments.yaml
```

### URL
Get file contents from a URL reference:

```yaml
sceptre_user_data:
  departments: !file https://my-bucket.s3.us-east-1.amazonaws.com/tags/departments.json
```
