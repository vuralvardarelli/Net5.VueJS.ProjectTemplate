# Net5.VueJS.ProjectTemplate
.Net Core 5.0 with VueJS Project Template

## Ready to Publish Template

## Steps
1. Go to folder clientapp and "npm install" inside the path.
2. That's all!! You are ready to debug or publish.

## Sample ".csproj" file

<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <RootNamespace>Net5.VueJS.ProjectTemplate</RootNamespace>
    <SpaRoot>clientapp\</SpaRoot>
    <DefaultItemExcludes>$(DefaultItemExcludes);$(SpaRoot)node_modules\**</DefaultItemExcludes>
    <BuildServerSideRenderer>false</BuildServerSideRenderer>
    <UserSecretsId>eb4adeef-c887-4382-810f-687138096c20</UserSecretsId>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="VueCliMiddleware" Version="5.0.0" />
  </ItemGroup>
  <ItemGroup>
    <Folder Include="Controllers\" />
  </ItemGroup>
  <Target Name="PublishRunWebpack" AfterTargets="ComputeFilesToPublish">
    <Exec WorkingDirectory="$(SpaRoot)" Command="npm install" />
    <Exec WorkingDirectory="$(SpaRoot)" Command="npm run build" />
    <ItemGroup>
      <DistFiles Include="$(SpaRoot)dist\**; $(SpaRoot)dist-server\**" />
      <DistFiles Include="$(SpaRoot)node_modules\**" Condition="'$(BuildServerSideRenderer)' == 'true'" />
      <ResolvedFileToPublish Include="@(DistFiles->'%(FullPath)')" Exclude="@(ResolvedFileToPublish)">
        <RelativePath>%(DistFiles.Identity)</RelativePath>
        <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
        <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
      </ResolvedFileToPublish>
    </ItemGroup>
  </Target>
</Project>
